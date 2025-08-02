---
created:
---

---
- [[0 Home]]
---

### 백업용 이전 코드

- SecurityConfig (25/8/10)
```
package com.techie.backend.global.security;  
  
import jakarta.servlet.http.HttpServletRequest;  
import jakarta.servlet.http.HttpServletResponse;  
import lombok.RequiredArgsConstructor;  
import org.slf4j.Logger;  
import org.slf4j.LoggerFactory;  
import org.springframework.context.annotation.Bean;  
import org.springframework.context.annotation.Configuration;  
import org.springframework.security.authentication.AuthenticationManager;  
import org.springframework.security.config.annotation.authentication.configuration.AuthenticationConfiguration;  
import org.springframework.security.config.annotation.web.builders.HttpSecurity;  
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;  
import org.springframework.security.config.annotation.web.configurers.AbstractHttpConfigurer;  
import org.springframework.security.config.http.SessionCreationPolicy;  
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;  
import org.springframework.security.web.SecurityFilterChain;  
import org.springframework.security.web.authentication.UsernamePasswordAuthenticationFilter;  
import org.springframework.web.cors.CorsConfiguration;  
import org.springframework.web.cors.CorsConfigurationSource;  
  
import java.util.Collections;  
  
@Configuration  
@EnableWebSecurity  
@RequiredArgsConstructor  
public class SecurityConfig {  
  
    private final AuthenticationConfiguration authenticationConfiguration;  
    private final JWTUtil jwtUtil;  
    private static final Logger log = LoggerFactory.getLogger(LoginFilter.class);  
  
  
    @Bean  
    public AuthenticationManager authenticationManager(AuthenticationConfiguration configuration) throws Exception {  
        return configuration.getAuthenticationManager();  
    }  
  
    @Bean  
    public BCryptPasswordEncoder passwordEncoder() {  
        return new BCryptPasswordEncoder(10);  
    }  
  
    @Bean  
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {  
        AuthenticationManager authManager = authenticationManager(authenticationConfiguration);  
  
        LoginFilter loginFilter = new LoginFilter(authManager, jwtUtil);  
        loginFilter.setFilterProcessesUrl("/login");  
  
        loginFilter.setAuthenticationFailureHandler((request, response, exception) -> {  
            log.error("❌ 커스텀 실패 핸들러 작동: {}", exception.getMessage(), exception);  
            response.setStatus(HttpServletResponse.SC_UNAUTHORIZED);  
            response.setContentType("application/json");  
            response.setCharacterEncoding("UTF-8");  
            response.getWriter().write("{\"error\": \"" + exception.getMessage() + "\"}");  
        });  
  
  
        http.csrf(AbstractHttpConfigurer::disable)  
                .formLogin(AbstractHttpConfigurer::disable)  
                .httpBasic(AbstractHttpConfigurer::disable)  
                .authorizeHttpRequests(auth -> {  
                    PathConfig.PERMIT_ALL_PATHS.forEach(path -> auth.requestMatchers(path).permitAll());  
                    PathConfig.AUTHENTICATED_PATHS.forEach(path -> auth.requestMatchers(path).authenticated());  
                    PathConfig.ADMIN_ONLY_PATHS.forEach(path -> auth.requestMatchers(path).hasRole("ADMIN"));  
                    auth.anyRequest().permitAll();  
                })  
                .addFilterBefore(new JWTFilter(jwtUtil), LoginFilter.class) // JWTFilter 먼저  
                .addFilterAt(loginFilter, UsernamePasswordAuthenticationFilter.class) // LoginFilter 등록  
                .sessionManagement(session -> session.sessionCreationPolicy(SessionCreationPolicy.STATELESS));  
  
        http.cors(corsCustomizer -> corsCustomizer.configurationSource(new CorsConfigurationSource() {  
            @Override  
            public CorsConfiguration getCorsConfiguration(HttpServletRequest request) {  
                CorsConfiguration configuration = new CorsConfiguration();  
                configuration.setAllowedOrigins(Collections.singletonList("http://localhost:3000"));  
                configuration.setAllowedMethods(Collections.singletonList("*"));  
                configuration.setAllowCredentials(true);  
                configuration.setAllowedHeaders(Collections.singletonList("*"));  
                configuration.setMaxAge(3600L);  
                configuration.setExposedHeaders(Collections.singletonList("Authorization"));  
                return configuration;  
            }  
        }));  
  
        return http.build();  
    }  
}
```
- LoginFilter ((25/8/10))
```
package com.techie.backend.global.security;  
  
import com.fasterxml.jackson.databind.ObjectMapper;  
import com.techie.backend.user.dto.UserRequest;  
import jakarta.servlet.FilterChain;  
import jakarta.servlet.http.HttpServletRequest;  
import jakarta.servlet.http.HttpServletResponse;  
import lombok.RequiredArgsConstructor;  
import org.springframework.security.authentication.*;  
import org.springframework.security.core.Authentication;  
import org.springframework.security.core.AuthenticationException;  
import org.springframework.security.core.GrantedAuthority;  
import org.springframework.security.core.userdetails.UsernameNotFoundException;  
import org.springframework.security.web.authentication.UsernamePasswordAuthenticationFilter;  
import org.slf4j.Logger;  
import org.slf4j.LoggerFactory;  
  
import java.util.Collection;  
import java.util.Iterator;  
import java.util.concurrent.atomic.AtomicInteger;  
  
@RequiredArgsConstructor  
public class LoginFilter extends UsernamePasswordAuthenticationFilter {  
    private final AuthenticationManager authenticationManager;  
    private final JWTUtil jwtUtil;  
    private final ObjectMapper objectMapper = new ObjectMapper();  
    private static final Logger log = LoggerFactory.getLogger(LoginFilter.class);  
  
  
    @Override  
    public Authentication attemptAuthentication(HttpServletRequest request, HttpServletResponse response) throws AuthenticationException {  
        String email = null;  
        String password = null;  
  
        try {  
            String contentType = request.getContentType();  
  
            if (contentType != null && contentType.startsWith("application/json")) {  
                UserRequest.Register loginRequest = objectMapper.readValue(request.getInputStream(), UserRequest.Register.class);  
                email = loginRequest.getEmail();  
                password = loginRequest.getPassword();  
            } else {  
                email = obtainUsername(request);  
                password = obtainPassword(request);  
            }  
  
            if (email == null || password == null) {  
                log.warn("❌ 로그인 시도 실패: email 또는 password가 null입니다.");  
                throw new BadCredentialsException("이메일 또는 비밀번호가 누락되었습니다.");  
            }  
  
        } catch (Exception e) {  
            log.error("❌ 로그인 요청 파싱 중 오류 발생", e);  
            throw new AuthenticationServiceException("요청 파싱 실패", e);  
        }  
  
        UsernamePasswordAuthenticationToken authToken = new UsernamePasswordAuthenticationToken(email, password, null);  
        return authenticationManager.authenticate(authToken);  
    }  
  
  
    @Override  
    protected void successfulAuthentication(HttpServletRequest request, HttpServletResponse response, FilterChain chain, Authentication authentication) {  
        UserDetailsCustom userDetailsCustom = (UserDetailsCustom) authentication.getPrincipal();  
  
        String email = userDetailsCustom.getUsername();  
        Collection<? extends GrantedAuthority> authorities = authentication.getAuthorities();  
        Iterator<? extends GrantedAuthority> iterator = authorities.iterator();  
        GrantedAuthority auth = iterator.next();  
        String role = auth.getAuthority();  
        String nickname = userDetailsCustom.getNickname();  
        String token = jwtUtil.createJwt(email, role, nickname, 3 * 60 * 60 * 1000L);  
  
//        log.info("✅ 로그인 성공: {}", email);  
  
        response.addHeader("Authorization", "Bearer " + token);  
    }  
  
    @Override  
    protected void unsuccessfulAuthentication(HttpServletRequest request,  
                                              HttpServletResponse response,  
                                              AuthenticationException failed) {  
        response.setStatus(HttpServletResponse.SC_UNAUTHORIZED);  
        response.setContentType("application/json");  
        response.setCharacterEncoding("UTF-8");  
  
  
        String errorMessage = "이메일 또는 비밀번호가 올바르지 않거나, 필수 입력란이 비어 있습니다.";  
  
        if (failed instanceof BadCredentialsException) {  
            errorMessage = "비밀번호가 일치하지 않습니다.";  
        } else if (failed instanceof UsernameNotFoundException) {  
            errorMessage = "존재하지 않는 이메일입니다.";  
        } else if (failed instanceof DisabledException) {  
            errorMessage = "비활성화된 계정입니다.";  
        } else if (failed instanceof LockedException) {  
            errorMessage = "잠긴 계정입니다.";  
        } else if (failed instanceof CredentialsExpiredException) {  
            errorMessage = "비밀번호 유효기간이 만료되었습니다.";  
        } else if (failed instanceof AuthenticationServiceException) {  
            errorMessage = failed.getMessage();  
        }  
        log.info("✅ 로그인 실패: {}", errorMessage);  
        log.error("❌ 로그인 실패 예외 발생", failed); // 스택트레이스 강제 출력  
  
    }  
}
```

---
### Build.gradle (25/08/02)

```
plugins {  
    id 'java'  
    id 'org.springframework.boot' version '3.3.4'  
    id 'io.spring.dependency-management' version '1.1.6'  
}  
  
group = 'com.techie'  
version = '0.0.1-SNAPSHOT'  
  
java {  
    toolchain {  
       languageVersion = JavaLanguageVersion.of(17)  
    }  
}  
  
configurations {  
    all {  
       exclude group: 'commons-logging', module: 'commons-logging'  
    }  
    compileOnly {  
       extendsFrom annotationProcessor  
    }  
}  
  
repositories {  
    mavenCentral()  
}  
  
dependencies {  
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa' // spring jpa  
    implementation 'org.springframework.boot:spring-boot-starter-security' // spring security  
    implementation 'org.springframework.boot:spring-boot-starter-web' // spring web  
    implementation group: 'org.modelmapper', name: 'modelmapper', version: '3.1.1' // modelmapper  
    implementation 'org.springdoc:springdoc-openapi-starter-webmvc-ui:2.0.2'  
    implementation 'com.querydsl:querydsl-jpa:5.0.0:jakarta'  
    implementation 'org.springframework.boot:spring-boot-starter-validation'  
    implementation 'org.springframework.boot:spring-boot-starter-actuator'  
    annotationProcessor "com.querydsl:querydsl-apt:${dependencyManagement.importedProperties['querydsl.version']}:jakarta"  
    annotationProcessor "jakarta.annotation:jakarta.annotation-api"  
    annotationProcessor "jakarta.persistence:jakarta.persistence-api"  
    compileOnly 'org.projectlombok:lombok'  
    developmentOnly 'org.springframework.boot:spring-boot-devtools'  
    runtimeOnly 'com.mysql:mysql-connector-j'  
    annotationProcessor 'org.projectlombok:lombok'  
    testImplementation 'org.springframework.boot:spring-boot-starter-test'  
    testImplementation 'org.springframework.security:spring-security-test'  
    testRuntimeOnly 'org.junit.platform:junit-platform-launcher'  
    // youtube api v3 ------  
    implementation 'com.google.api-client:google-api-client:1.33.0'  
    implementation 'com.google.apis:google-api-services-youtube:v3-rev20230816-2.0.0'  
    implementation 'com.google.http-client:google-http-client-jackson2:1.39.2'  
    // gpt api  
    implementation 'org.apache.httpcomponents.client5:httpclient5:5.2'  
    implementation 'org.apache.httpcomponents.core5:httpcore5:5.2'  
    testImplementation 'junit:junit:4.13.2'  
    // jwt  
    implementation 'io.jsonwebtoken:jjwt-api:0.12.3'  
    runtimeOnly 'io.jsonwebtoken:jjwt-impl:0.12.3'  
    runtimeOnly 'io.jsonwebtoken:jjwt-jackson:0.12.3'  
//  implementation 'io.jsonwebtoken:jjwt-api:0.12.3'  
//  implementation 'io.jsonwebtoken:jjwt-impl:0.12.3'  
//  implementation 'io.jsonwebtoken:jjwt-jackson:0.12.3'  
  
    // argon2    implementation 'org.bouncycastle:bcprov-jdk15to18:1.70'  
    // Actuator  
    implementation 'org.springframework.boot:spring-boot-starter-actuator'  
}  
  
def generated = 'build/generated'  
  
tasks.withType(JavaCompile) {  
    options.generatedSourceOutputDirectory = file(generated)  
}  
  
sourceSets {  
    main.java.srcDirs += "$projectDir/build/generated"  
}  
  
clean {  
    delete file('build/generated')  
}  
  
tasks.named('test') {  
    useJUnitPlatform()  
}  
tasks.withType(JavaCompile) {  
    options.compilerArgs << "-parameters"  
}
```

---
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
import lombok.RequiredArgsConstructor;  
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
        http.csrf(AbstractHttpConfigurer::disable)  
                .formLogin(AbstractHttpConfigurer::disable)  
                .httpBasic(AbstractHttpConfigurer::disable)  
                .authorizeHttpRequests(auth -> {  
                    PathConfig.PERMIT_ALL_PATHS.forEach(path -> auth.requestMatchers(path).permitAll());  
                    PathConfig.AUTHENTICATED_PATHS.forEach(path -> auth.requestMatchers(path).authenticated());  
                    PathConfig.ADMIN_ONLY_PATHS.forEach(path -> auth.requestMatchers(path).hasRole("ADMIN"));  
                    auth.anyRequest().permitAll();  
                })  
                .addFilterBefore(new JWTFilter(jwtUtil), LoginFilter.class)  
                .addFilterAt(new LoginFilter(authenticationManager(authenticationConfiguration), jwtUtil), UsernamePasswordAuthenticationFilter.class)  
                .sessionManagement((session) -> session  
                        .sessionCreationPolicy(SessionCreationPolicy.STATELESS));  
        http  
                .cors((corsCustomizer -> corsCustomizer.configurationSource(new CorsConfigurationSource() {  
  
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
                })));  
  
        return http.build();  
    }  
}
```
- LoginFilter ((25/8/10))
```
@Override  
public Authentication attemptAuthentication(HttpServletRequest request, HttpServletResponse response) throws AuthenticationException {  
    String email = null;  
    String password = null;  
  
    try {  
        if ("application/json".equals(request.getContentType())) {  
            UserRequest.Register loginRequest = objectMapper.readValue(request.getInputStream(), UserRequest.Register.class);  
            email = loginRequest.getEmail();  
            password = loginRequest.getPassword();  
        } else {  
            email = obtainUsername(request);  
            password = obtainPassword(request);  
        }  
    } catch (Exception e) {  
        e.printStackTrace();  
    }  
  
    UsernamePasswordAuthenticationToken authToken = new UsernamePasswordAuthenticationToken(email, password, null);  
    return authenticationManager.authenticate(authToken);  
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
---
created:
---
---
# **README**

- domain
``` java
// 패키지 선언 - 이 경로 내에서 클래스가 위치함을 나타낸다.
package com.techie.backend.gpt.domain;  
// User 클래스를 불러와 이 파일에 사용할 수 있도록 한다.
import com.techie.backend.user.domain.User; 
// jpa 관련 어노테이션들을 포함한 패키지 
// 이 파일로 데이터베이스 관련 기능을 사용할 수 있다.
import jakarta.persistence.*; 
// lombok 라이브러리 제공 어노테이션
// 자동으로 Getter를 생성해준다.
import lombok.Getter;  
// lobok 라이브러리 제공 어노테이션
// 기본 생성자 (파라미터가 없는 생성자)를 자동으로 생성한다.
// 객체 생성 시 생성자 코드를 작성 하지 않아도 되는 장점이 있다.
import lombok.NoArgsConstructor;  

@NoArgsConstructor  
@Getter  
@Entity  
@Table(name = "gpt")  
public class Gpt {  
  
    @Id  
    @GeneratedValue(strategy = GenerationType.IDENTITY)  
    private long id;  
  
    @Column(nullable = false)  
    private String request;  
  
    @Column(nullable = false)  
    private String response;  
  
    @JoinColumn(name = "user_id", nullable = false)  
    @ManyToOne(fetch = FetchType.LAZY)  
    private User user;  
  
    public void updateRequest(String request) {  
        this.request = request;  
    }  
  
    public void updateResponse(String response) {  
        this.response = response;  
    }  
  
    public void assignUser(User user) {  
        this.user = user;  
    }  
  
}
```


##### GPT
- 
``` java


  



// DTO

package com.techie.backend.gpt.dto;  
  
import lombok.Data;  
  
@Data  
public class GptRequest {  
    private String request;  
}

package com.techie.backend.gpt.dto;  
  
import lombok.Data;  
  
@Data  
public class GptResponse {  
    private String request;  
    private String response;  
}

// Repository
package com.techie.backend.gpt.repository;  
  
import com.techie.backend.gpt.domain.Gpt;  
import org.springframework.data.jpa.repository.JpaRepository;  
import org.springframework.stereotype.Repository;  
  
@Repository  
public interface GptRepository extends JpaRepository<Gpt, Long>, GptRepositoryCustom {  
}

package com.techie.backend.gpt.repository;  
  
  
public interface GptRepositoryCustom {  
}


package com.techie.backend.gpt.repository;  
  
import lombok.RequiredArgsConstructor;  
  
@RequiredArgsConstructor  
public class GptRepositoryImpl implements GptRepositoryCustom {  
}


//Service
package com.techie.backend.gpt.service;  
  
import com.techie.backend.gpt.dto.GptRequest;  
import com.techie.backend.gpt.dto.GptResponse;  
import org.springframework.http.ResponseEntity;  
import org.springframework.stereotype.Service;  
  
public interface GptService {  
    ResponseEntity<GptResponse> questionAndAnswer(GptRequest gptRequest);  
}

package com.techie.backend.gpt.service;  
  
import com.fasterxml.jackson.databind.JsonNode;  
import com.fasterxml.jackson.databind.ObjectMapper;  
import com.techie.backend.gpt.domain.Gpt;  
import com.techie.backend.gpt.dto.GptRequest;  
import com.techie.backend.gpt.dto.GptResponse;  
import com.techie.backend.gpt.repository.GptRepository;  
import lombok.RequiredArgsConstructor;  
import org.apache.hc.client5.http.classic.methods.HttpPost;  
import org.apache.hc.client5.http.impl.classic.CloseableHttpClient;  
import org.apache.hc.client5.http.impl.classic.CloseableHttpResponse;  
import org.apache.hc.client5.http.impl.classic.HttpClients;  
import org.apache.hc.core5.http.ContentType;  
import org.apache.hc.core5.http.ParseException;  
import org.apache.hc.core5.http.io.entity.EntityUtils;  
import org.apache.hc.core5.http.io.entity.StringEntity;  
import org.slf4j.Logger;  
import org.slf4j.LoggerFactory;  
import org.springframework.beans.factory.annotation.Value;  
import org.springframework.http.HttpStatus;  
import org.springframework.http.ResponseEntity;  
import org.springframework.stereotype.Service;  
  
import java.io.IOException;  
import java.util.HashMap;  
import java.util.List;  
import java.util.Map;  
  
@Service  
@RequiredArgsConstructor  
public class GptServiceImpl implements GptService {  
  
    private static final Logger logger = LoggerFactory.getLogger(GptServiceImpl.class);  
  
    private final ObjectMapper objectMapper;  
    private final GptRepository gptRepository;  
  
    @Value("${openai.api.key}")  
    private String API_KEY;  
    @Value("${openai.api.url}")  
    private String API_URL;  
  
    @Override  
    public ResponseEntity<GptResponse> questionAndAnswer(GptRequest gptRequest) {  
        String request = gptRequest.getRequest();  
  
        if (request == null || request.isEmpty()) {  
            throw new IllegalArgumentException("The GPT request cannot be null or empty");  
        }  
  
        try (CloseableHttpClient httpClient = HttpClients.createDefault()) {  
            HttpPost httpPost = new HttpPost(API_URL);  
            httpPost.setHeader("Authorization", "Bearer " + API_KEY);  
            httpPost.setHeader("Content-Type", "application/json");  
  
            Map<String, Object> body = new HashMap<>();  
            body.put("model", "gpt-3.5-turbo");  
            body.put("messages", List.of(Map.of("role", "user", "content", request)));  
  
            StringEntity entity = new StringEntity(objectMapper.writeValueAsString(body), ContentType.APPLICATION_JSON);  
            httpPost.setEntity(entity);  
  
            try (CloseableHttpResponse response = httpClient.execute(httpPost)) {  
                int statusCode = response.getCode();  
                String responseBody = EntityUtils.toString(response.getEntity());  
  
                if (statusCode != HttpStatus.OK.value()) {  
                    logger.error("Response Status Code: {}", statusCode);  
                    throw new RuntimeException("Failed to get a response from GPT. Status code: " + statusCode);  
                }  
  
                JsonNode rootNode = objectMapper.readTree(responseBody);  
                String gptContent = rootNode.path("choices").get(0).path("message").path("content").asText();  
  
                Gpt gpt = new Gpt();  
                gpt.updateRequest(request);  
                gpt.updateResponse(gptContent);  
                gptRepository.save(gpt);  
  
                GptResponse gptResponse = new GptResponse();  
                gptResponse.setRequest(request);  
                gptResponse.setResponse(gptContent);  
  
                return new ResponseEntity<>(gptResponse, HttpStatus.OK);  
            } catch (ParseException e) {  
                throw new RuntimeException("Error parsing the GPT response", e);  
            }  
        } catch (IOException e) {  
            throw new RuntimeException(e);  
        }  
    }  
}

package com.techie.backend.gpt.controller;  
  
import com.techie.backend.gpt.dto.GptRequest;  
import com.techie.backend.gpt.dto.GptResponse;  
import com.techie.backend.gpt.service.GptService;  
import lombok.RequiredArgsConstructor;  
import org.springframework.http.ResponseEntity;  
import org.springframework.web.bind.annotation.PostMapping;  
import org.springframework.web.bind.annotation.RequestBody;  
import org.springframework.web.bind.annotation.RequestMapping;  
import org.springframework.web.bind.annotation.RestController;  
  
@RestController  
@RequestMapping("/api/gpt")  
@RequiredArgsConstructor  
public class GptController {  
    private final GptService gptService;  
  
    @PostMapping("/qna")  
    public ResponseEntity<GptResponse> questionAndAnswer(@RequestBody GptRequest gptRequest) {  
        return gptService.questionAndAnswer(gptRequest);  
    }  
}



```


- 
``` java

```

- 
``` java

```
- 
``` java

```


# 양식
- 
``` java

```
- 
``` java

```

- 
``` java

```
- 
``` java

```

- 
``` java

```

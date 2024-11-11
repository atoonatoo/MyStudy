---
created:
---
---
# **README**

### gradle.build
### gpt json 타입 postman 

```
// 리퀘스트
{
  "model": "gpt-3.5-turbo",
  "messages": [
    {"role": "user", "content": "에덴 동산 최초의 인간은? 답변만해"}
  ],
  "temperature": 1,
  "max_tokens": 10
}

//리스폰

{
    "id": "chatcmpl-ALMUIkBL4a2lAqWDJFL0QiUvuBL1F",
    "object": "chat.completion",
    "created": 1729654694,
    "model": "gpt-3.5-turbo-0125",
    "choices": [

        {

            "index": 0,

            "message": {

                "role": "assistant",

                "content": "아담과 이브입니다.",

                "refusal": null

            },

            "logprobs": null,

            "finish_reason": "stop"

        }

    ],

    "usage": {

        "prompt_tokens": 27,

        "completion_tokens": 9,

        "total_tokens": 36,

        "prompt_tokens_details": {

            "cached_tokens": 0

        },

        "completion_tokens_details": {

            "reasoning_tokens": 0

        }

    },

    "system_fingerprint": null

}
```



### GPT 코드

- domain
``` java
// gpt api  
implementation 'org.apache.httpcomponents.client5:httpclient5:5.2'  
implementation 'org.apache.httpcomponents.core5:httpcore5:5.2'  
testImplementation 'junit:junit:4.13.2'

//domain
import com.techie.backend.user.domain.User;  
import jakarta.persistence.*;  
import lombok.Getter;  
import lombok.NoArgsConstructor;  
import lombok.Setter;  
  
@NoArgsConstructor  
@Getter  
@Setter  
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
}

// dto request
package com.techie.backend.gpt.dto;  
  
import lombok.Data;  
  
@Data  
public class GptRequest {  
    private String request;  
}

// dto response
package com.techie.backend.gpt.dto;  
  
import lombok.Data;  
  
@Data  
public class GptResponse {  
    private String request;  
    private String response;  
}

// repository


//repositorycustom


//repositoryimpl
package com.techie.backend.gpt.repository;  
  
import lombok.RequiredArgsConstructor;  
import org.springframework.stereotype.Repository;  
  
@Repository  
@RequiredArgsConstructor  
public class GptRepositoryImpl implements GptRepositoryCustom {  
}

//service
package com.techie.backend.gpt.service;  
  
import com.techie.backend.gpt.dto.GptRequest;  
import com.techie.backend.gpt.dto.GptResponse;  
import org.springframework.http.ResponseEntity;  
import org.springframework.stereotype.Service;  
  
@Service  
public interface GptService {  
    ResponseEntity<GptResponse> questionAndAnswer(GptRequest gptRequest);  
}

//serviceimpl
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
  
                Gpt gptHistory = new Gpt();  
                gptHistory.setRequest(request);  
                gptHistory.setResponse(gptContent);  
                gptRepository.save(gptHistory);  
  
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

//controller
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

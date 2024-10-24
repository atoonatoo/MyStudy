---
created:
---
---
# **README**


### GPT 질문 예시

- **`stream()`**: "모든 사람의 이름을 차례로 가져와!"
- **`map()`**: "이 사람 이름을 다른 형태로 바꿔줘!"
- **`collect()`**: "바꾼 결과들을 다시 리스트로 만들어서 나한테 줘!"

이렇게 `stream()`을 사용하면 **데이터를 쉽게 변환**하고 **리스트로 모을 수** 있어서 코드가 더 짧고 간결해집니다.


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
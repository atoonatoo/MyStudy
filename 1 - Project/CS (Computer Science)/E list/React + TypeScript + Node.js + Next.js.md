---
created: 2024-01-04
updated: 2024-09-23
---
----
##### 연결 문서

- 
- 
- 
---

# **README**

### **타입 스크립트 기본 설치 및 설정
##### 1. **Next.js 프로젝트 생성**

Next.js 프로젝트를 생성합니다. `npx create-next-app@latest` 명령어를 사용하면 Next.js 앱을 생성할 수 있습니다.

```bash
npx create-next-app@latest my-next-app
cd my-next-app
```

- **`my-next-app`**: 프로젝트 폴더 이름입니다. 원하는 이름으로 변경 가능합니다.
- **디렉토리 이동**: 프로젝트 생성 후, 해당 디렉토리로 이동합니다.

##### 2. **TypeScript 설치**

Next.js는 TypeScript를 자동으로 지원하지만, 명시적으로 TypeScript를 설치하고 설정하려면 다음 명령어를 실행합니다.

```bash
npm install --save-dev typescript @types/react @types/node
```

- **typescript**: TypeScript 컴파일러
- **@types/react**: React의 TypeScript 타입 정의
- **@types/node**: Node.js의 TypeScript 타입 정의


##### 3. **TypeScript 설정 파일 생성**

TypeScript 파일을 프로젝트에 추가하면 Next.js가 자동으로 `tsconfig.json` 파일을 생성합니다. 
수동으로 생성하고 싶다면 다음 명령어를 사용합니다.
```bash
npx tsc --init
```

##### 4. **폴더 구조 설정**

Next.js의 기본적인 폴더 구조에 **`components/`** 폴더를 추가하여 재사용 가능한 컴포넌트를 관리할 수 있습니다.

```bash
my-next-app/
├── app/
│   ├── components/
│   │   └── Header.tsx    # 헤더 컴포넌트
│   └── pages/
│       └── api/          # API 엔드포인트
│           └── hello.ts  # /api/hello
├── public/               # 정적 파일 (이미지, 폰트 등)
├── tsconfig.json         # TypeScript 설정 파일
└── .env.local            # 환경 변수 파일

```

##### 5. **ESLint 및 Prettier 설정**

코드 품질을 유지하기 위해 ESLint와 Prettier를 설정할 수 있습니다.

```bash
npm install --save-dev eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
npx eslint --init

```

- ESlint 설정 예시

```bash
{
  "extends": [
    "next/core-web-vitals",
    "plugin:@typescript-eslint/recommended"
  ],
  "parser": "@typescript-eslint/parser",
  "plugins": ["@typescript-eslint"],
  "rules": {
    "@typescript-eslint/no-unused-vars": "error",
    "react/react-in-jsx-scope": "off"
  }
}

```

##### 6. **환경 변수 설정**

**`.env.local`** 파일을 프로젝트 루트에 생성해 환경 변수를 설정할 수 있습니다. 이 파일은 로컬 개발 환경에서만 적용됩니다.

**`NEXT_PUBLIC_API_URL`**과 같은 환경 변수를 설정:

```bash
# .env.local
NEXT_PUBLIC_API_URL=http://localhost:3000

```
이 파일을 사용하면 **로컬 개발 환경**에서만 적용되는 환경 변수를 관리할 수 있습니다.


##### 7. **API 라우팅 설정**

Next.js에서 API 엔드포인트를 정의하려면 **`pages/api`** 디렉토리에 파일을 추가합니다.

**예시: `/api/hello` API 라우트**

```bash
// pages/api/hello.ts
import { NextApiRequest, NextApiResponse } from 'next';

export default function handler(req: NextApiRequest, res: NextApiResponse) {
  res.status(200).json({ message: 'Hello, World!' });
}

```

##### 8. **프로젝트 실행**

모든 설정이 완료되었으면, Next.js 개발 서버를 실행하여 프로젝트를 확인할 수 있습니다.


```bash
npm run dev
```


##### 요약:

1. **Next.js 프로젝트 생성**: `npx create-next-app@latest my-next-app`
2. **TypeScript 설치**: `npm install --save-dev typescript @types/react @types/node`
3. **ESLint 및 Prettier 설정**: 코드 스타일과 린트 규칙 적용
4. **환경 변수 설정**: `.env.local` 파일 생성
5. **API 설정**: `pages/api`에 API 라우트 추가
6. **프로젝트 실행**: `npm run dev`

이 과정대로 설정하면, Next.js와 TypeScript 기반의 프로젝트를 성공적으로 시작할 수 있습니다.

### **타입스크립트의 기본 개념**

- import { useState } from 'react';
	- 리액트에 자주 사용되는 개념으로 hook을 가져오는 부분이다.
	  
##### hook이란?

- React에서 Hook이란 특정 시점에서 동작하도록 함수를 호출할 수 있게 해주는 메커니즘이다.
- Hook의 의미는 프레임워크의 흐름에 나의 코드를 연결해서 특정 타이밍에 실행되도록 걸어두는 것
- 즉 특정 API 매핑 주소를 호출할 경우 실행되는 메서드와 유사한 방식
- 차이점
	- React Hook은 setData같은 특정 상태가 변경될 경우 실행
- Java Method는 API 호출할 경우 해당 메서드 실행
##### useState란?
- **상태(state)를 괸리하기 위한 Hook
- 백엔드 자바의 getter, setter의 대응하는 개념
- 리액트의 useState가 이 역할을 한다. 
- 리액트는 상태가 바뀔때마다  UI(화면)을 자동으로 업데이트한다. 

```js
const [username, setUsername] = useState('');
```

- username : 현재 값
- setUsername : 상태가 변경하는 함수

- 백엔드에서 setter를 호출하면 필드 값이 업데이트되는 것처럼, 
- React에서 `setUsername('new value')`을 호출하면 UI가 자동으로 갱신된다.
```js
useEffect(() => {
  // 이 코드는 컴포넌트가 처음 렌더링될 때 실행됩니다.
  console.log('Component mounted');

  // 컴포넌트가 사라질 때 실행되는 정리(clean-up) 함수
  return () => {
    console.log('Component unmounted');
  };
}, []);
```

- 백엔드에서 컨트롤러가 초기화될 때 수행하는 작업처럼, 
- `useEffect`는 프론트엔드 컴포넌트가 화면에 나타날 때 또는 특정 이벤트가 발생할 때 동작한다.


##### useEffect

- 컴포넌트의 생명주기(lifecycle)를 관리하는 Hook
- 데이터 가져오기, DOM 조작, 구독 설정 및 해제와 같은 컴포넌트 외부의 작업 포함
- 주요개념
	- **부수효과** : 상태나 , UI 변경과는 직접 관련이 없지만, 컴포넌트가 랜더링될 때 또는 상태가 변경될 때 추가로 발생해야 하는 작업들이다.
	- 예를 들어 서버에서 데이터를 가져오거나, 타이머를 설정하거나, 구독을 설정할 떄 사용된다.
- 기본 사용법

```JS
useEffect(() => {
  // 여기에 들어가는 코드는 렌더링 시 실행됩니다.
  console.log('컴포넌트가 렌더링되었습니다.');
}, []);  // 빈 배열: 컴포넌트가 처음 렌더링될 때 한 번만 실행

```

- useEfeect는 컴포넌트가 랜더링될 때마다 실행
- 배열을 사용해 의존성을 관리할 수 있다.
- 만약 의존성 배열에 값이 있다면, 그 값이 변경될 떄만 useEffect

- 예시
```js
import { useState, useEffect } from 'react';

const DataFetching = () => {
  const [data, setData] = useState(null);

  useEffect(() => {
    // 데이터 가져오기 예시
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setData(data));
  }, []);  // 빈 배열: 컴포넌트가 처음 렌더링될 때 한 번만 실행

  return (
    <div>
      {data ? <p>{data}</p> : <p>Loading...</p>}
    </div>
  );
};

```

- 컴포넌트가 처음 렌더링될 때 `useEffect`가 실행되어 데이터를 서버에서 가져옵니다.
- **의존성 배열**에 빈 배열 `[]`이 있으므로, 컴포넌트가 처음 화면에 나타날 때 한 번만 실행됩니다.

- UseEffect 뒤에 , 와 []의 역할
	- 의존성 배열이라고 부르며, 이 배열 안에 들어간 값들이 변경될 때만 useEffect  내부의 함수가 실행되도록 하는 역할
	  
	- 빈 배열의 의미
		- 초기상태를 설정하고 싶을 때
		  
	- 의존성 배열의 의미
		- 특정 상태가 변경될 때만 실행되게끔
		- 랜더링 후에도 특정 상태나 props가 변할 떄만 useEffect가 실행되도록 \
		- 즉, 화면에 바로 등장하지 않다가, 의존성 배열이 들어간 상태가 변경될 떄 그제서야 useEffect가 실행되면 랜더리엥 변화를 줄 수 있다.
		  
	- **예시 : 데이터가 로드될 때만 UI 업데이트**
```js
const [data, setData] = useState(null);

useEffect(() => {
  if (data) {
    console.log('데이터가 변경되었을 때만 이 코드가 실행됩니다.');
  }
}, [data]);  // data가 변경될 때만 useEffect 실행

return (
  <div>
    {data ? <p>Data: {data}</p> : <p>Loading...</p>}
  </div>
);

```

##### 프론트와 백엔드의 연결

- 백엔드에서 로그인이나 데이터베이스 작업을 처리할 때, 프론트에서 **HTTP 요청**을 통해 데이터를 전달한다.
- **axios**로 로그인 요청을 보내는 부분이 바로 그 예이다.
- 자바 백엔드에서 처리할 때도 @PostMapping으로 데이터를 받아 처리하는 것처럼, 프론트에서는 axios.post()를 통해 데이터를 보낸다.
- 이부분은 백엔드에서 Contorller나 Service와 상호작용하는 방식과 유사하다.

- **요약
	- `useState`는 백엔드의 필드 변수와 setter 역할.
	- `useEffect`는 백엔드의 생명주기 관리 (`@PostConstruct`, `@PreDestroy`)와 비슷.
	- `axios`는 백엔드의 `RestTemplate`이나 `WebClient`처럼 HTTP 요청을 처리하는 역할.

##### React와 TypeScript의 차이점

###### TypeScript란?

- JavaScript의 상위 집합
- 정적 타임 검사를 추가한 언어
- **JavaScript 코드에 타입 시스템을 도입**하여 코드의 오류를 미리 잡고 더 견고한 코드를 작성할 수 있도록 도와준다.
- 모든 JavaScript는 유효한 TypeScript 코드이다.

###### TypeScript 주요 특징

- 정적 타입 시스템
	- 코드를 작성할 때 변수, 함수, 객체 등에 타입을 명시할 수 있다.
	- 실행전 타입 오류를 잡을 수 있다.
- 개발 도구 지원
	- 타입 정보가 명하기 떄문에 IDE에서 더 나은 **자동완성**과 코드 오류 감지 기능을 제공
- ES6 + 기능 지원 
	- 최신 ECMScript(ES6+) 기능을 지원하고, 이를 브라우저 호환성이 좋은 버전으로 트랜스 파일링할 수 있다.


###### React란?

- 사용자 인터페이스(UI)를 구축하기 위한 라이브러리
- 주로 컴포넌트 기반으로 동적인 웹 페이지를 쉽게 만들 수 있게 도와준다.
- React 자체는 타입 시스템이 없다.
- JavaScript를 기본으로 사용한다.
###### React 특징

- 컴포넌트 기반
	- 작은 단위의 컴포넌트를 만들어 재사용 가능하고 유지보수하기 쉬운 코드 작성 가능
- 상태 관리
	- 컴포넌트 내부에서 상태를 관리하고, 상태가 변경될 때마다 UI가 자동으로 업데이트 된다.

###### 왜 TypeScirpt를  React와 함꼐 사용하는가?

- React는 JavaScript로도 잘 동작하지만, TypeScript를 추가로 사용하면 몇 가지 큰 장점이 있다.

- 타입 안전성 제공
	- JS는 **동적 타입 언어**라서 변수나, 함수의 타입이 실행중에 결정된다.
	- 이는 유연하지만, 런타임 오류가 발생한 가능성이 높다.
	- 반면, TS는 **정적 타입 언어**로, 컴파일 단계에서 타입을 미리 체크해 오류를 방지한다.
	  
- 예시
```TS
const greet = (name: string): string => {
  return `Hello, ${name}!`;
};

// 숫자를 넣으면 TypeScript에서 오류를 미리 잡아줌
greet(42);  // 오류 발생: 'number' 타입은 'string' 타입에 할당할 수 없음
```

- React와 함꼐 TS를 사용하면 컴포넌트의 props나 state에 대한 타입을 명시할 수 있어, 실수를 줄이고 코드의 가독성을 높인다.


- 코드 자동 완성 및 IDE 지원
	- TS는 코드 작성 시 자동 완성과 정확한 함수 호출을 도와준다.
	- React는 props나 state를 많이 사용하는데 TS 덕분에 어떤 props가 필요한지, 함수가 어떤 타입의 인자를 받는지 명확하게 알 수 있다. 
	
- 예시
```TS
interface ButtonProps {
  label: string;
  onClick: () => void;
}

const Button = ({ label, onClick }: ButtonProps) => (
  <button onClick={onClick}>{label}</button>
);

// 자동 완성으로 'label'과 'onClick'에 대한 타입 정보를 얻을 수 있음
<Button label="Submit" onClick={() => console.log('Clicked!')} />

```

- 위처럼, TS는 인터페이스를 통해 컴포넌트의 props를 명확하게 정의할 수 있어, 잘못된 props를 넘기는 실수를 방지한다.

###### React와 TS의 결합 예시
```TS
import React, { useState } from 'react';

interface CounterProps {
  initialCount: number;
}

const Counter = ({ initialCount }: CounterProps) => {
  const [count, setCount] = useState<number>(initialCount);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};

export default Counter;
```



##### props란

- properties의 줄임말
- **React 컴포넌트 간 데이터를 전달**하는 방법
- React에서 부모 컴포넌트가 자식 컴포넌트에게 데이터를 전달할 때 사용
- 즉, 컴포넌트 외부에서 전달받는 값

###### 주요 개념

- 데이터 전달
	- 부모 컴포넌트가 자식 컴포넌트에 데이터(상태, 값, 함수 등)을 전달하기 위한 수단
- 읽기 전용
	- 자식 컴포넌트는 props로 전달받은 값을 **직접 수정할 수 없다**.
	- 부모가 전달한 값은 **자식 컴포넌트에서 읽기만** 할 수 있다.
		- **변경은 부모 컴포넌트**에서 해야한다.
- 예시
```ts
const ChildComponent = (props: { message: string }) => {
  return <h1>{props.message}</h1>;
};

const ParentComponent = () => {
  const greeting = "Hello, world!";
  return <ChildComponent message={greeting} />;
};

```
###### 역할과 기능

- 데이터 전달
	- 컴포넌트 간에 데이터를 전달하고, 이를 통해 부모 컴포넌트와 자식 컴포넌트가 상호작용할 수 있게 도와준다.
- 동적 랜더링
	- 부모가 전달하는 props에 따라 자식 컴포넌트의 동작이나 출력이 달라질 수 있다.
- 재사용성
	- props를 통해 컴포넌트를 더 재사용 가능하게 만들 수 있다.
	- 같은 컴포넌트를 다른 값으로 호출할 수 있다.

###### props의 Java 백엔드 개념과 비교

- 메서드의 매개변수와 대응한다.
```JAVA
public class GreetingService {
    public String getGreeting(String name) {
        return "Hello, " + name;
    }
}
```

- 여기서 name은 메서드 getyGreeting의 매개변수이다.
- Java 메서드의 매개변수처럼, React의 props도 컴포넌트가 외부에서 값을 받아 사용하는 방식으로 동작

- props는 부모가 자식에게 값을 전달하는 구조이고, Java의 메서드 매개변수는 외부에서 메서드로 값을 전달하는 구조라는 점에서 유사하다.

###### props와 state의 차이

- React에서 자주 햇갈리는 개념 중 하나가 props와 state의 차이이다.
- 두 개념 모두 컴포넌트 값을 관리하지만, 그 역할과 관리 방식이 다르다.

- props
	- **부모 컴포넌트가 자식 컴포넌트에게 전달하는 외부 데이터**
	- **읽기 전용**, 자식 컴포넌트는 props를 변경할 수 없다.
	- 데이터는 **상위 컴포넌트에서 내려오는 구조**이다.
- state
	- **컴포넌트 내부에서 관리하는 데이터**
	- **자체적으로 변경**할 수 있다. 변경될 때마다 컴포넌트가 다시 렌더링된다.
	- 상태 변화는 **컴포넌트 내부에서** 발생한다.

- 예시 비교
```ts
// props 예시: 부모가 자식에게 데이터를 전달
const Child = ({ message }: { message: string }) => <p>{message}</p>;

const Parent = () => <Child message="Hello, props!" />;

// state 예시: 컴포넌트 내부에서 관리하는 값
const Counter = () => {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>{count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};
```


##### props의 컴포넌트 전달 방식 응용

###### 1. **`props`**는:

- **부모 컴포넌트**가 **자식 컴포넌트**에 **읽기 전용**으로 데이터를 전달하는 방식.
- 자식은 `props`를 **수정할 수 없지만**, 부모로부터 상태 변경 함수를 함께 전달하면 **수정 가능**하게 만들 수 있음.

###### 2. **다른 컴포넌트 간 데이터 전달**:

- **형제 컴포넌트 간** 데이터를 공유하려면 **공통 부모** 컴포넌트에서 상태를 관리하고, `props`로 전달.
- **전역 상태 관리**를 위해서는 **Context API**나 **Redux** 같은 전역 상태 관리 라이브러리를 사용.

###### 3. **전역 상태 관리**:

- **Context API**: 컴포넌트 트리 전체에서 **부모-자식 관계 없이** 데이터를 공유.
- **Redux**: 대규모 애플리케이션에서 **중앙 상태 관리**를 위한 강력한 도구.

요약하면, `props`는 데이터를 전달할 때 유용하지만 **수정 불가능**하다는 제한이 있습니다. 수정 가능하게 하려면 **상태와 상태 변경 함수**를 함께 전달하거나, **Context API/Redux**를 사용해 **전역적으로 상태를 관리**할 수 있습니다.

##### axios 

- 브라우저나 Node.js 환경에서 HTTP 요청을 보낼 수 있게 해주는 JS 라이브러리
- 주로 비동기적으로 서버와 데이터를 주고받기 위해 사용
- React 같은 프론트엔드 어플리케이션에서 API 요청을 쉽게 처리할 수 있도록 도와준다.

##### async

- 비동기 함수를 정의할 때 사용하는 키워드
- 즉, 이 힘수는 다른 작업을 기다리면서도 멈추지 않고 계속해서 실행될 수 있도록한다.
- 비동기 프로그래밍은 특히 네트워크 요청이나 파일 읽기와 같이 시간이 오래 걸릴 수 있는 작업을 처리할 때 유용
###### async의 사용하는 이유
- 예시 : 로그인을 할 때 백엔드 서버에 요청을 보내고 그 결과가 돌아올 떄까지 시간이 걸릴수 있다.
- 만약 이 시간이 걸리는 동안 프로그램이 멈추면, 사용자 경험이 좋지 않다.
- 그래서 비동기 방식으로 요청을 보내고, 요청이 완료되기를 기다리면서도 다른 작업을 처리할 수 있게 해준다.

###### 동작 방식
- `async` 키워드는 함수 앞에 붙어서 그 함수를 **비동기함수**로 만들어준다.
- 이 함수는 내부에서 ``await``를 사용할 수 있는데, `await`는 비동기 작업이 끝날 때까지 기다리도록 만든다.
- 그러면서도 전체 프로그램은 계속해서 실행된다.
```ts
const handleLogin = async (e: React.FormEvent) => {
  // 비동기 함수로 선언됨
  e.preventDefault();
  
  try {
    // 백엔드에 요청을 보낸 후, 그 결과를 기다림
    const response = await axios.post('http://localhost:8080/api/users/auth', {
      username,
      password,
    });

    // 서버에서 응답을 받으면 그때 아래 코드 실행
    if (response.status === 200) {
      alert('Login successful!');
      router.push('/home');
    }
  } catch (error) {
    alert('Login failed. Please check your credentials.');
  }
};

```

###### 핵심 정리
- async
	- 바동기 함수를 정의하는 키워드
- await
	- 비동기 작업이 완료될 때까지 기다리게 하지만, 그동안 다른 코드 실행은 계속된다.
```ts
const handleLogin = async (e: React.FormEvent) => {
  e.preventDefault();

  try {
    // await으로 axios 요청의 결과가 올 때까지 기다림
    const response = await axios.post('http://localhost:8080/api/users/auth', {
      username,
      password,
    });

    if (response.status === 200) {
      alert('Login successful!');
      router.push('/home');
    }
  } catch (error) {
    alert('Login failed. Please check your credentials.');
  }
};


// await 없이 처리하는 방법 (대체 방식)

const handleLogin = (e: React.FormEvent) => {
  e.preventDefault();

  axios
    .post('http://localhost:8080/api/users/auth', {
      username,
      password,
    })
    .then((response) => {
      if (response.status === 200) {
        alert('Login successful!');
        router.push('/home');
      }
    })
    .catch((error) => {
      alert('Login failed. Please check your credentials.');
    });
};


```
- 네트워크 요청이나 파일 읽기 같은 시간이 걸리는 작업에 유용

###### 주요 역할과 기능

- HTTP 요청 보내기
	- GET, POST, PUT, DELETE 같은 HTTP 메서드를 사용해 서버에 요청을 보낸다.
	- 예를 들어 서버에서 데이터를 가져오거나(API 요청)
	- 서버로 데이터를 전송 (폼 제출)할 수 있다.
	
- 예시
```JS
axios.get('https://api.example.com/data')
  .then(response => console.log(response.data))
  .catch(error => console.error(error));
```
	
- Promise 기반
	- axios는 Promise를 사용하여 비동기 작업을 처리한다.
	- 요청이 완료되면 **.then()** 으로 응답을 처리하고, 오류가 발생하면 **.catch()** 로 처리할 수 있다.
	  
- 응답 데이터 자동 변환
	- 서버에서 받은 데이터를 JSON 형태로 자동 변환해주므로 추가 처리가 필요 없다.
	
- 헤더 설정
	- 요청 시 **헤더(Header)** 를 설정여 인증 토큰이나 콘텐츠 타입을 지정할 수 있다.
	
- 예시
```js
axios.post('https://api.example.com/login', { username, password }, {
  headers: { 'Content-Type': 'application/json' }
});
```
	
- 에러 처리
	- 요청에 실패했을 때 오류 처리를 쉽게 할 수 있으며, 응답 코드에 따라 다르게 처리할 수 있다.
	
- 요약
	- axios는 HTTP 요청을 쉽게 보낼 수 있는 비동기 통신 라이브러리
	- Promise 기반으로 동작하며 데이터 전송과 API 호출을 매우 간편하게 처리
	- 주로 GET, POST 요청을 통해 서버와 데이터를 주고받고, 헤더 설정과 오류 처리도 지원

##### React.FormEvent, React.preventDefault

- React.FormEvent
	- React에서 제공하는 이벤트 객체의 타입
	- 주로 Form과 관련된 이벤트 (제출, 입력, 변경)를 처리할 때 사용
	- 예시로 폼이 제출될 때 `onSubmit` 핸들러에서 이벤트 객체를 전달받는데, 그 타입이 `React.FormEvent`이다.
	- `event`는 브라우저에서 발생한 이벤트를 나타내는 객체
	- `React.FormEvent`는 폼과 관련된 이벤트를 다룰 떄 사용
	- 예시로 폼 제출, 텍스트 입력 등과 관련된 이벤트에 대해 구체적인 정보 
	  
- prventDefault()
	- 브라우저가 기본적으로 수행하는 동작을 **막는 메서드**
	- 예를 들어, 폼이 제출되면, 브라우저는 기본적으로 페이지를 새로고침하려고 한다.
	- 그러나 이 기본 동작을 막고, JS나  React에서 정의된 동작을 실행하고 싶을 때 `preventDefault()`를 사용한다.
	
- 예시
```ts
const handleSubmit = (event: React.FormEvent) => {
  event.preventDefault(); // 기본적으로 페이지가 새로고침되는 것을 막음
  // 서버로 데이터를 보낸다거나, 상태를 업데이트하는 등의 동작을 추가
};
```

- prventDefault()가 필요한 이유
	- 기본적으로 폼을 제출하면 페이지가 새로고침되면서 폼 데이터가 서버에 전송된다.
	- 하지만 싱글 페이지 애플리케이션(SPA)에서는 전체 페이지를 새로고침하지 않고, JS 코드로만 폼 제출을 처리하고 싶을 떄가 많다.
	- 이떄 `preventDefault()`를 사용해서 **기본 새로고침을 방지**하고
	- 서버에 **AJAX 요청**이나 **API 호출**을 통해 데이터를 처리할 수 있다.


###### 정리

- React.FormEvent
	- 폼 관련 이벤트 객체의 타입을 지정하여, TypeScript가 타입 검사를 할 수 있게 도와준다. 
	- 주로 폼 제출이나 입력 이벤트를 처리할 때 사용된다.
- event.preventDefault()
	- 폼 제출 후 발생하는 **기본적인 새로고침 동작을 막아** 사용자 정의 작업을 실행할 수 있게 해준다.


##### Node.js

- JS 런타임 환경으로, 브라우저 외부에서 서버 측에서 JS 코드를 실행할 수 있도록 해준다.
- 즉, **서버를 JS로 구현** 할 수 있게 해주는 기술이다.

###### 주요 역할

- 백엔드 개발
	- Node js를 사용해 서버를 만들고, 데이터베이스와 연동하거나 API 요청을 처리
	- 비동기 I/O 처리
		- 빠른 입출력을 처리하기 적합
		- 주로 실시간 어플리케이션이나 API 서버 개발에 많이 사용
	
- 예시
```JS
const http = require('http');
const server = http.createServer((req, res) => {
  res.end('Hello from Node.js server!');
});
server.listen(3000);
```

- Node js는 서버에서 JS를 실행하고 클라이언트의 요청을 처리
#### Next.js

- Next js는 React 기반의 프레임워크
- 서버 사이드 랜더링 (SSR), 정적 사이트 생성, 라우팅 기능 제공
- 프론트 엔드 개발에서 React를 더 확장하여 서버에서 랜더링된 HTML을 반환하거나 SEO를 강화할 수 있다.

###### 주요 역할
- 서버 사이드 랜더링 (SSR)
	- React 어플리케이션을 서버에서 랜더링해 빠르게 초기 화면을 보야주고 SEO에 최적화
	- 정적 사이트 생성 (SSG)
		- 빌드 시점에 HTML 파일을 생성해 성능을 향상시키는 방식
	- 라우팅 시스템
		- 페이지 파일을 자동으로 라우팅하고, 동적 경로도 쉽게 관리 할 수 있다.
	
- 예시
```JS
const Home = () => {
  return <h1>Hello from Next.js!</h1>;
};

export default Home;
```

- Next.js는 **React 컴포넌트**를 사용해 **서버 사이드 렌더링**과 **정적 페이지 생성**을 쉽게 처리합니다.

###### 차이점

- Node js
	- **서버에서 JS 실행 환경 제공**
	- 주로 **백엔드 개발**에 사용
	
- Next js
	- React 기반 프레임워크로 프론트엔드 개발에 사용
	- 서버 사이드 랜더링(SSR) 및 정적 사이트 생성(SSG)을 통해 SEO를 개선
  
  
###### 추가 질문 해답

-   **Node.js** 관련 질문:
	- Node.js가 브라우저 외부에서 서버 측에서 JS 코드를 실행할 수 있도록 해준다는 의미
		- js는 원래 브라우저에서만 동작하는 언어
		- 즉, 클라이언트 측(브라우저)에서만 HTML CSS를 조작하는 용도로 사용
		- 하지만 Node js 는 브라우저 외부에서, 즉 서버측에서도 JS를 실행할 수 있는 런타임 환경 제공
		- 이로 인해 서버에서 JS로 웹 서버를 구축하거나 , 파일 시스템에 접근하는 등 다양한 작업 가능
	
	- 서버에서 JavaScript를 구현할 경우 장점
		- 하나의 언어로 풀스택 개발 가능
			- 프론트 백 모두 JS로 작성할 수 있어 동일한 언어로 클라이언트, 서버를 다룰 수 있다.
			- 이는 학습 곡선을 줄이고 개발속도를 높인다.
		- 비동기 I/O를 처리
			- Node js는 비동기 방식을 지원한다.
			- 때문에 많은 클라이언트 요청을 효율적으로 처리할 수 있다.
			- 실시간 어플리케이션(채팅, 알림)에 적합하다.
		- 빠른 속도 처리
			- V8  JS 엔진을 기반으로 하고 있어 빠르고, 이벤트 기반 아키텍처 덕분에 성능이 뛰어나다.
	
- 서버 사이드 랜더링 (SSR) 관련 질문
	  
	- 서버에서 렌더링한다는 의미:
		- React 어플리케이션을 서버에서 미리 렌더링하여 완성된 HTML파일을 클라이언트에 전달하는 방식
		- 일반적인 React 어플리케이션은 브라우저에서 처음 랜더링 될 때 JS 파일을 다운로드하고, 브라우저에서 랜더링을 시작
		- SSR을 사용하면 서버에서 이미 완성된 HTML을 렌더링하여 브라우저에 전송하기 때문에, 초기 화면이 더 빠르게 보이게 된다.
	- SEO란?
		- SEO(Search Engine Optimization)는 검색 엔진 최적화를 의미
		- 구글 같은 검색 엔진이 웹사이트를 잘 읽고 분석할 수 있도록 돕는 방법
  
- 정적 사이트 생성(SSG) 관련 질문
  
	- 정적 사이트 생성한다는 의미
		- 빌드 시점에서 HTML 파일을 미리 생성하는 방식
		- 이 HTML 파일은 고정된 콘텐츠를 포함
		- 서버에서 추가적인 렌더링 작업 없이 정적 HMTL을 제공
		- 즉, 정적 파일로 웹사이트를 미리 생성해두고 클라이언트에 제공하는 방식
	- 빌드 시점에 HTML을 생성하면 성능이 향상되는 이유
		- 정적사이트는 서버에서 동적으로 데이터를 처리하거나 렌더링할 필요가 없기 떄문에, 서버 부하가 적고 페이지 로딩 속도가 매우 빠르다.
	- 모든 HTML이 미리 생성되어 있기 떄문에 서버가 요청을 받을 때 바로 HTML을 전달할 수 있다.


###### 라우팅 시스템 관련 질문

- 라우팅이란?
	- **URL에 따라 다른 페이지 또는 다른 컴포넌트로 렌더링하는 것을의미**
	- 예를 들어, 사욘자가 `/about` 페이지에 접근하면 `About` 컴포넌트를 렌더링하고, `/home`에 접근하면 `Home` 컴포넌트를 렌더링하는 방식
- 동적 경로 쉽게 괸리하는 예시
	- Next js는 동적 경로를 매우 쉽게 설정 가능
	- 예시로 블로그 게시글의 ID가 동적인 경우, URL에 따라 다른 게시글을 렌더링 할 수 있다.
```TS
// pages/posts/[id].tsx
const Post = ({ id }) => {
  return <div>Post ID: {id}</div>;
};

export async function getServerSideProps(context) {
  return { props: { id: context.params.id } };
}

export default Post;

```

- Next js 간단한 페이지 만들기 예시의 의미
	- 예시 코드는 Next js에서 페이지를 만드는 방식을 보여준다.
	- Next js는 파일 기반 라우팅 시스템을 사용하므로, `pages` 디렉토리 파일에 생성하면 그 파일이 자동으로 페이디 URL에 매핑된다.
	  
```TS
const Home = () => {
  return <h1>Hello from Next.js!</h1>;
};

export default Home;
```

- 이 코드는 `pages/index.tsx`에 작성하면, 브라우저에서 `localhost:3000/`으로 접근했을 때 **자동으로 이 페이지가 렌더링**된다.


##### 요약:

- **Node.js**는 **브라우저 외부에서 서버 측에서 JavaScript**를 실행할 수 있게 해주는 기술로, 서버를 JavaScript로 구현할 수 있습니다.

- **SSR**은 **서버에서 미리 HTML을 렌더링**하여 더 빠른 초기 화면과 SEO 최적화를 제공합니다.
  
- **SSG**는 **빌드 시점에 HTML을 미리 생성**하여 서버 부하를 줄이고 성능을 높이는 방식입니다.
  
- **라우팅**은 URL에 따라 다른 페이지를 렌더링하는 방식이며, **동적 경로**는 URL에 따라 다른 데이터를 렌더링할 수 있게 합니다.
  
- Next.js는 **파일 기반 라우팅**과 **SSR, SSG**를 지원하는 프레임워크로, **간단한 코드**로 페이지를 만들고 관리할 수 있습니다.



### TypeScript 구조


##### 기본 디렉토리 구조
```ruby
my-nextjs-app/
│
├── pages/                   # 페이지별 라우팅을 처리하는 디렉토리
│   ├── index.tsx            # 메인 페이지 (예: 홈 화면)
│   ├── about.tsx            # about 페이지
│   └── api/                 # API 라우팅을 위한 폴더
│       └── hello.ts         # API 엔드포인트
│
├── components/              # 재사용 가능한 UI 컴포넌트
│   └── Header.tsx
│   └── Footer.tsx
│
├── public/                  # 정적 파일 (이미지, 아이콘 등)
│   └── images/
│
├── styles/                  # 전역 스타일 시트 (CSS/SCSS)
│   └── global.css
│   └── Home.module.css      # 모듈화된 스타일 시트
│
├── types/                   # 타입 정의를 위한 폴더
│   └── index.d.ts           # 전역 타입 정의 파일
│
├── utils/                   # 유틸리티 함수 및 헬퍼 함수
│   └── fetcher.ts           # 데이터 패칭 관련 함수
│
├── .next/                   # Next.js가 빌드 중 생성하는 폴더 (자동 생성됨)
├── node_modules/            # 설치된 패키지
├── next.config.js           # Next.js 설정 파일
├── tsconfig.json            # TypeScript 설정 파일
└── package.json             # 프로젝트 설정 및 종속성

```

##### 각 디렉토리의 설명

- pages/
	- Next js 파일 기반 라우팅을 담당하는 디렉토리
	- 각 파일은 해당 경로에 해당하는 페이지로 렌더링
	- 예시로 `about.tsx`는 `/about` 경로로 접근할 수 있다.
- api/
	- API 엔드포인트를 정의하는 곳이다.
	- 서버 측에서 실행되는 API 함수를 여기에 정의할 수 있다.
- components/
	- 재사용 가능 한 UI 컴포넌트를 저장하는 곳
	- 예를 들어, Header나 Footer와 같은 부분들을 정의
- public/
	- 정적 파일(이미지, 폰트 등)을 저장하는 디렉토리
	- 이곳의 파일은 `/public` 경로로 접근
- styles/
	- CSS 파일을 저장하는 곳
	- 전역 스타일과 모듈 스타일을 포함
	- CSS 모듈을 사용하면 특정 컴포넌트에만 적용되는 CSS 파일을 만들 수 있다.
- types/
	- TypeScript에서 사용하는 **타입 정의파일**을 저장하는 디렉토리
	- 전역 타입이나 인터페이스를 선언할 떄 이 폴더를 사용
- utils/
	- 데이터 처리나 API 요청 등 **유틸리티 함수**를 정의하는 곳
	- 비지니스 로직과는 독립적인 헬퍼 함수들이 포함
- tsconfig.json
	- TypeScript 설정 파일
	- 프로젝트 내의 TypeScript 설정을 정의
	- 여기에서 **타입체크**나 **컴파일 옵션**을 설정
	
- 이 구조는 Next.js TypeScript 프로젝트에서 코드의 가독성과 유지보수성을 높이기 위한 표준적인 방식




### TypeScript 로그인 예제 코드


1. 타입 정의 (`types/`)
	- 로그인 요청 및 응답 데이터의 타입 정의
	- 타입 정의는 TS에서 정적 타입 체크를 할 수 있게 해준다.
```ts
// types/auth.ts
export interface LoginRequest {
  username: string;
  password: string;
}

export interface LoginResponse {
  token: string;       // 서버에서 반환하는 JWT 토큰
  userId: number;
}
```

2. API 요청 함수 (`utils/`)
	- API 요청 처리하는 유틸리티 함수 작성
	- 이 함수는 서버에 로그인 요청을 보내고, 서버로부터 받은 응답을 처리
```ts
// utils/api.ts
import axios from 'axios';
import { LoginRequest, LoginResponse } from '../types/auth';

export const login = async (data: LoginRequest): Promise<LoginResponse> => {
  try {
    const response = await axios.post<LoginResponse>('https://api.example.com/login', data);
    return response.data;  // 타입이 명확하게 지정됨
  } catch (error) {
    throw new Error('Login failed');
  }
};
```
- `axios.post<LoginResponse>`
	- 서버로부터 받은 응답 타입을 명확하게 지정
	- 이로 인해 서버에서 예상하지 못한 데이터가 반환될 경우, TS가 컴파일 시점에서 오류를 감지

3. 정의 (`components/LoginForm.tsx`)
	- React 컴포넌트에서 **useState**를 사용해 폼 데이터를 관리하고, **로그인 버튼**을 눌렀을 때 API 요청을 보낸다.
```ts
// components/LoginForm.tsx
import { useState } from 'react';
import { login } from '../utils/api';
import { LoginRequest } from '../types/auth';

const LoginForm = () => {
  const [username, setUsername] = useState<string>('');
  const [password, setPassword] = useState<string>('');
  const [error, setError] = useState<string | null>(null);

  const handleSubmit = async (event: React.FormEvent) => {
    event.preventDefault();

    const loginData: LoginRequest = { username, password }; // 타입 명시적 지정
    try {
      const response = await login(loginData);
      console.log('Login successful:', response.token);
      // 로그인 성공 후 처리 (예: 토큰 저장, 리다이렉트 등)
    } catch (error) {
      setError('Login failed. Please try again.');
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label>Username:</label>
        <input
          type="text"
          value={username}
          onChange={(e) => setUsername(e.target.value)}
          required
        />
      </div>
      <div>
        <label>Password:</label>
        <input
          type="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
          required
        />
      </div>
      {error && <p>{error}</p>}
      <button type="submit">Login</button>
    </form>
  );
};

export default LoginForm;

```
	
4. 동작 구조 설명
	- 상태 관리
		- `useState`를 사용해 로그인 폼에 입력된 `usernmae`, `password`를 관리
		- 사용자가 로그인 폼에 값을 입력하면, 상태가 업데이트된다.
	- API 요청 처리
		- 로그인 버튼을 누르면, `handleSubmit` 함수가 호출되고 폼에서 입력된 데이터를 **타입에 맞게 요청 객체로 변환**
		- `login` 함수가 호출되어 서버로 API 요청을 보내고, 응답으로 받은 **JWT 토큰을 받아 처리
	- 타입 안전성
		- `LoginRequest`와 `LoginResponse` 타입을 사용해 데이터의 구조를 명확히 정의하여 **타입 오류**를 방지
		- **서버로부터 예상치 못한 데이터**가 올 경우, TS는 컴파일 단계에서 오류를 감지할 수 있어 **런타임 오류를 줄일 수 있다.
	
5. 요약
	- TS는 서버와의 통신에 요청 데아터와 응답 데이터의 타입을 명확하게 정의함으로써, 타입 안전성을 보장한다.
	- 로그인 API 요청에 TS는 서버에서 받은 데이터를 올바르게 처리할 수 있도록 타입을 검사하고, 오류를 사전에 방지해 준다.
---
description: React Server Component (RSC)
---

# 서버 컴포넌트(Server Component)

### 서버 컴포넌트가 필요한 이유

React는 서버에서 렌더링 할 수 있는 컴포넌트인 RSC를 제공함으로써 개발자가 원하는 곳에서 컴포넌트를 렌더링 할 수 있는 선택지를 제공한다고 설명합니다.&#x20;

기존의 Server Side Rendering(SSR)과 다른 점을 간단하게 정리하자면 SSR은 서버에서 페이지 단위로 정적인 리소스를 생성하지만 RSC는 컴포넌트 단위로 정적인 리소스를 생성할 수 있다는 점입니다.

{% hint style="info" %}
SSR = 서버 -> 페이지 단위

RSC = 컴포넌트 단위
{% endhint %}

여기서 RSC의 가장 큰 장점이 나옵니다.&#x20;

클라이언트로 내려보내는 JavaScript 번들 크기를 줄일 수 있게 되는 것이죠. 뿐만아니라 데이터베이스와 보다 가까운 곳에서 데이터를 조회하기 때문에 속도도 더 빨라질 수 있습니다.&#x20;

이는 PHP, Ruby on Rails와 유사하지만 우리에게 익숙한 React라는 라이브러리를 활용할 수 있다는 점에서 매력적이죠. 이러한 장점 덕분에 Next.js에서는 RSC를 기본 컴포넌트 렌더링 방식으로 채택하고 있습니다.&#x20;

하지만 모든 컴포넌트를 RSC로 만들 순 없습니다.



### 서버 컴포넌트 혹은 클라이언트 컴포넌트

브라우저 API를 사용하거나 `useState`, `useEffect` 등의 훅을 이용해야하는 경우에는 여전히 클라이언트 컴포넌트를 사용해야하죠. 이럴 땐 파일 가장 첫 줄에 `'use client'`라고 명시해야 합니다.

```tsx
'use client'
 
import { useState } from 'react'
 
export default function Counter() {
  const [count, setCount] = useState(0)
 
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  )
}
```

아래의 표는 서버 컴포넌트와 클라이언트 컴포넌트를 사용해야 하는 경우를 구분 지어뒀습니다. ([출처](https://nextjs.org/docs/getting-started/react-essentials#when-to-use-server-and-client-components))

| 원하는 것                                        | 서버 컴포넌트 | 클라이언트 컴포넌트 |
| -------------------------------------------- | ------- | ---------- |
| 데이터 가져오기                                     | ✅       | ✘          |
| 백엔드 리소스에 직접 접근하기                             | ✅       | ✘          |
| 민감한 정보를 서버에 보관할 때(액세스 토큰, API 키 등)           | ✅       | ✘          |
| JavaScript 리소스 줄이기                           | ✅       | ✘          |
| 상호작용 및 이벤트 리스너(`onClick`, `onChange` 등) 사용하기 | ✘       | ✅          |
| 상태 및 생애 주기 관리(`useState`, `useEffect` 등)     | ✘       | ✅          |
| 브라우저 API 사용하기                                | ✘       | ✅          |
| React 클래스 컴포넌트 사용하기                          | ✘       | ✅          |



### 서버 컴포넌트 활용 패턴

"아니, 뭐야 `useState`, `useEffect` 같은 훅을 사용하지 못하고 이벤트 리스너도 사용하지 못하면 자주 쓸 일이 있긴 한거야?" 하는 생각이 드실겁니다. 그래서 Next.js에선 클라이언트 컴포넌트를 최대한 말단(Leaves)으로 내려보내길 권합니다.

클라이언트 컴포넌트를 최대한 말단으로 내려보내라는 건 서버 컴포넌트에서 클라이언트 컴포넌트를 불러오는 동작은 문제가 없다는 것을 의미합니다. 반면, 클라이언트 컴포넌트에서 서버 컴포넌트를 불러오는 패턴은 지원되지 않습니다.

아래의 코드는 동작하지 않는 예시입니다. ([출처](https://nextjs.org/docs/getting-started/react-essentials#unsupported-pattern-importing-server-components-into-client-components))

```tsx
'use client'
 
// 이 패턴은 동작하지 않습니다.
// 클라이언트 컴포넌트에서 서버 컴포넌트를 불러오기 할 수 없습니다.
import ExampleServerComponent from './example-server-component'
 
export default function ExampleClientComponent({
  children,
}: {
  children: React.ReactNode
}) {
  const [count, setCount] = useState(0)
 
  return (
    <>
      <button onClick={() => setCount(count + 1)}>{count}</button>
 
      <ExampleServerComponent />
    </>
  )
}
```

직접 불러올 순 없지만 자식 요소(children)로 전달할 순 있습니다.

```tsx
'use client'
 
import { useState } from 'react'
 
export default function ExampleClientComponent({
  children, // 서버 컴포넌트를 자식 요소로 전달할 수 있습니다.
}: {
  children: React.ReactNode
}) {
  const [count, setCount] = useState(0)
 
  return (
    <>
      <button onClick={() => setCount(count + 1)}>{count}</button>
 
      {children}
    </>
  )
}
```












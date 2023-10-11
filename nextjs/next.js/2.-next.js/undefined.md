---
description: 페이지 간 이동하는 방법
---

# 페이지 이동

앞서 세그먼트를 정하고 파일을 만들어서 실제로 접근할 수 있는 페이지를 만들었습니다. 그럼 각 페이지 간에 이동은 어떻게 구현할까요?

### `<Link>` 컴포넌트 사용하기

`<Link>` 컴포넌트는 HTML `<a>` 태그의 확장된 버전입니다. 페이지 이동 전에 필요한 미리 데이터를 페칭하는 프리페칭(pre-fetching) 기능을 지원하죠.&#x20;

```tsx
import Link from 'next/link'
 
export default function Page() {
  return <Link href="/dashboard">Dashboard</Link>
}
```



### `useRouter()` Hook 사용하기

`<a>` 태그를 사용하기 어려운 순간도 있습니다. 버튼 컴포넌트를 클릭해서 이동해야 하는 경우도 많죠.&#x20;

이럴 땐 `useRouter`를 사용하면 됩니다. 한 가지 알아두셔야 할 점은 `useRouter`가 **클라이언트 컴포넌트에서만 사용할 수 있다는 점**입니다.

```tsx
'use client'
 
import { useRouter } from 'next/navigation'
 
export default function Page() {
  const router = useRouter()
 
  return (
    <button type="button" onClick={() => router.push('/dashboard')}>
      Dashboard
    </button>
  )
}
```
















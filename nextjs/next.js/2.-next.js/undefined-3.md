---
description: metadata
---

# 메타데이터

Next.js에서는 메타데이터(Metadata)를 설정하는 두 가지 방법이 있습니다.&#x20;

설정 기반 메타데이터(Config-based Metadata)와 파일 기반 메타데이터(File-based Metadata)가 그 방법입니다.

설정 기반 메타데이터 방식에는 **정적 방식**(Static Metadata)과 **동적 방식**(Dynamic Metadata)이 있습니다.



### 정적 메타데이터

정적 방식은 Metadata 객체를 정의하는 방식입니다.

{% code title="layout.tsx 혹은 page.tsx" %}
```tsx
import type { Metadata } from 'next'
 
export const metadata: Metadata = {
  title: '...',
  description: '...',
}
 
export default function Page() {}
```
{% endcode %}

1. metadata라는 이름의 객체를 만들고, 그 객체를 Metadata라는 타입을 지정합니다.
2. 해당 객체를 외부로 export 시켜줍니다.
3. 객체 안에 있는 값이 페이지 metadata로 변환됩니다.



### 동적 메타데이터

동적 방식은 `generateMetadata`라는 함수를 이용해 동적으로 Metadata 객체를 생성하는 방식입니다.

metadata를 하나하나씩 지정하지 않고, 블로그의 내용에 따라 지정해주고 싶을 때 동적 방식을 사용하면 됩니다.

예를 들어 블로그 내용을 기반으로 metadata를 생성하고 싶다면 아래 코드를 참고해주세요:

{% code title="app/blog/[id]/page.tsx" %}
```tsx
import type { Metadata, ResolvingMetadata } from 'next'
 
type Props = {
  params: { id: string }
  searchParams: { [key: string]: string | string[] | undefined }
}
 
export async function generateMetadata(
  { params, searchParams }: Props,
  parent?: ResolvingMetadata
): Promise<Metadata> {
  const id = params.id
  
  const post = await fetch(`https://.../${id}`).then((res) => res.json())
  
  const previousImages = (await parent).openGraph?.images || []
 
  return {
    title: post.title,
    openGraph: {
      images: ['/some-specific-page-image.jpg', ...previousImages],
    },
  }
}
 
export default function Page({ params, searchParams }: Props) {}
```
{% endcode %}

1. generateMetadata 인자로 동적 라우팅에서 받았던 값을 작성해줍니다.
2. 해당 인자 값으로 fetch를 진행합니다.
3. 블로그의 내용을 가져옵니다.
4. 블로그의 내용을 metadat로 return 합니다.




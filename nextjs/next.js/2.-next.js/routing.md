---
description: 경로 지정하기
---

# 라우팅(Routing)

라우팅은 쉽게 말해 '경로 지정하기'라고 부르면 적절할 것 같습니다. 웹 어플리케이션에서 경로란 URL Path를 의미합니다.&#x20;

Next.js에선 파일 시스템으로 경로를 지정하는데요. 무슨 의미인지 살펴보겠습니다.



### 폴더 이름을 따르는 URL Path

Next.js의 파일 시스템 기반의 라우팅은 아래와 같은 형태를 이룹니다.

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

`app`이라는 폴더를 만들고 그 아래 `dashboard`, `settings`라는 폴더를 만들면 URL path가 폴더 이름과 동일한 순서를 따라 만들어집니다.&#x20;

루트 라우트 세그먼트 이름을 `app`이라고 지으면 App Router, `pages`라고 지으면 Pages Router가 됩니다.&#x20;



### 상황에 따라 짓는 파일 이름

세그먼트에는 파일이 필요합니다. Next.js에서는 상황에 맞는 UI를 정의할 때 쓰는 파일명이 미리 정해져있습니다.

<table data-header-hidden><thead><tr><th width="179.5">파일명</th><th>동작</th></tr></thead><tbody><tr><td><a href="https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#layouts"><code>layout</code></a></td><td>세그먼트의 메인 컨텐츠와 하위 세그먼트의 공용 레이아웃 UI</td></tr><tr><td><a href="https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#pages"><code>page</code></a></td><td>세그먼트의 메인 컨텐츠 UI</td></tr><tr><td><a href="https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming"><code>loading</code></a></td><td>세그먼트의 메인 컨텐츠와 하위 세그먼트의 로딩 UI</td></tr><tr><td><a href="https://nextjs.org/docs/app/api-reference/file-conventions/not-found"><code>not-found</code></a></td><td>세그먼트의 메인 컨텐츠와 하위 세그먼트의 Not Found UI</td></tr><tr><td><a href="https://nextjs.org/docs/app/building-your-application/routing/error-handling"><code>error</code></a></td><td>세그먼트의 메인 컨텐츠와 하위 세그먼트의 에러 UI</td></tr><tr><td><a href="https://nextjs.org/docs/app/building-your-application/routing/error-handling"><code>global-error</code></a></td><td>전역 에러 UI</td></tr><tr><td><a href="https://nextjs.org/docs/app/building-your-application/routing/route-handlers"><code>route</code></a></td><td>서버 API 엔드포인트</td></tr><tr><td><a href="https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#templates"><code>template</code></a></td><td>특별하게 재사용될 수 있는 레이아웃 UI</td></tr><tr><td><a href="https://nextjs.org/docs/app/api-reference/file-conventions/default"><code>default</code></a></td><td>패러럴 라우트의 폴백 UI</td></tr></tbody></table>

아래의 이미지를 보시면 파일 이름을 약속된대로 지정해서 세그먼트 안에 정의하면 Next.js가 알아서 React 컴포넌트를 배치해주는거죠.

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

위에서 언급한 파일명 이외에는 아무 이름이나 넣어도 라우트에 영향을 주지 않습니다. 필요에 따라 다양한 파일을 추가해도 괜찮다는 의미죠.



### 동적으로 변할 수 있는 URL Path 만들기

블로그를 만든다고 가정하면 게시글마다 ID 혹은 이름을 갖습니다. 블로그 상세 페이지라면 `/blog/:id` 와 같은 형태를 갖는 것이죠. 이런 경우를 위해 Next.js에서는 [Dynamic Routes](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes)라는 기능을 제공합니다.&#x20;

Dynamic Routes는 파일 이름을 대괄호로 묶어주는 걸 약속으로 합니다. 대괄호 안에 지정한 이름을 Page 컴포넌트의 인자로 받을 수 있습니다.

{% code title="app/blog/[id]/page.tsx" %}
```tsx
export default function Page({ params }: { params: { id: string } }) {
  return <div>My Post: {params.id}</div>
}
```
{% endcode %}






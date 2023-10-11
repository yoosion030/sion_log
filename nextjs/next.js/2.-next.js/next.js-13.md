---
description: Next.js 12와 13의 다른 점
---

# Next.js 13

### Next.js 13의 변화

**파일 시스템 기반 라우팅**은 Next.js의 핵심 기능 중 하나 입니다. 이전 버전까지는 `pages`라는 디렉토리 아래에 폴더와 파일을 규칙에 맞게 넣으면 라우팅 구조를 만들 수 있었습니다.&#x20;

2022년 10월 25일에 열린 [Next.js Conf](https://nextjs.org/conf)에서 소개된 Next.js 13에서는 `app`이라는 디렉토리로 만드는 라우팅도 함께 지원합니다. 이걸 **App Router**라고 부릅니다. 처음 공개된 App Router는 [app directory](https://nextjs.org/blog/next-13#new-app-directory-beta)라는 이름으로 소개됐습니다. 이후 [13.4 버전](https://nextjs.org/blog/next-13-4#nextjs-app-router)에서 안정화되면서 App Router로 이름을 확정짓습니다.

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

표면적으로 `pages`와 `app` 은 달라보이지 않습니다. 구조가 비슷하기 때문이죠.&#x20;

하지만 실제로 App Router는 React 18의 `React Sever Component(RSC)`, `Suspense`를 기본적으로 염두한 방식입니다. (Next.js 팀은 Meta의 React 코어 팀과 긴밀하게 협업해서 React의 최신 기능을 Next.js에 빠르게 적용했다고 합니다.)



### App Router

App Router는 Page Router보다 구성이 보다 간결해졌습니다. 보다 직관적인 디렉토리 구성이 가능해졌죠. 기존에는 `_app`, `_docuemnt` 같은 디렉토리를 두면서 레이아웃을 잡고 공통의 스타일을 적용해야 했습니다.

뿐만 아니라 `Suspense`를 사용해 hydration을 컴포넌트 단위로 수행할 수 있게 됐습니다. 이를 [`Streaming`](https://nextjs.org/blog/next-13#streaming)이라고 부릅니다. 쉽게 표현하자면 데이터가 준비되는만큼 미리 그려둘 수 있게 된 것입니다.&#x20;

이전에는 Server Side Rendering을 할 때 데이터가 모두 준비될 때까지 기다렸다가 전체 UI를 그려야했거든요. 이는 유저에게 의미있는 컨텐츠를 제공하는 속도를 단축하는 결과를 낳게되죠.

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>






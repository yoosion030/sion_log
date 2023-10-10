# Introduction

### What is Next.js ?

Next.js는 풀스택 웹 애플리케이션을 구축하기 위한 React 프레임워크입니다. React 컴포넌트를 사용하여 사용자 인터페이스를 구축하고, Next.js를 사용하여 추가 기능과 최적화를 수행할 수 있습니다.

내부적으로 Next.js는 번들링, 컴파일 등과 같이 React에 필요한 도구를 추상화 하고 자동으로 구성합니다. 이를 통해 구성에 시간을 낭비하지 않고 애플리케이션 구축에 집중할 수 있습니다.

개인 개발자이든 대규모 팀의 일원이든 Next.js는 상호적이고, 동적이며 빠른 React 애플리케이션을 구축할 수 있습니다.



### Main Features

Next.js의 주요 기능 중 일부는 다음과 같습니다.

<table><thead><tr><th width="129.5">Feature</th><th>Description</th></tr></thead><tbody><tr><td>Routing</td><td>파일 시스템 기반으로 레이아웃, 중첩 라우팅, 로딩 상태, 에러 핸들링 등을 지원하는 서버 컴포넌트입니다.</td></tr><tr><td>Rendering</td><td>클라이언트 및 서버 컴포넌트를 사용한 클라이언트 측 및 서버 측 렌더링. Next.js를 사용하여 서버에서 정적 및 동적 렌더링으로 더욱 최적화되었습니다. Edge 및 Node.js 런타임에서 스트리밍합니다.</td></tr><tr><td>Data Fetching</td><td>서버 컴포넌트의 async/await를 사용하여 데이터 가져오기를 단순화하고 요청 메모이제이션, 데이터 캐싱 및 재요청을 위한 확장된 fetch API를 제공합니다.</td></tr><tr><td>Styling</td><td>CSS 모듈, Tailwind CSS, CSS-in-JS 등 선호하는 스타일 지정 방법 지원.</td></tr><tr><td>Optimizations</td><td>애플리케이션의 핵심 웹 성능 및 사용자 경험을 개선하기 위한 이미지, 글꼴 및 스크립트 최적화.</td></tr><tr><td>TypeScript</td><td>더 나은 타입 검사, 더 효율적인 컴파일, 사용자 정의 TypeScript 플러그인 및 타입 체커를 통해 TypeScript에 대한 지원이 향상되었습니다.</td></tr></tbody></table>



### How to User These Docs

화면 왼쪽에는 문서 탐색 모음이 있습니다. 문서의 페이지는 기본부터 심화까지 순차적으로 구성되어 있으므로 애플리케이션을 구축할 때 단계별로 따라갈 수 있습니다.

그러나 순서에 관계없이 페이지를 건너뛸 수 있습니다.

화면 오른쪽에는 페이지 섹션 간을 더 쉽게 탐색할 수 있는 목차가 표시됩니다. 페이지를 빠르게 찾아야 하는 경우 상단의 검색창을 이용하거나 검색 바로가기`(Ctrl+K 또는 Cmd+K)`를 이용하세요.

###

### App Router vs Pages Router

Next.js에는 앱 라우터(App Router)와 페이지 라우터(Pages Router)라는 두 가지 라우터가 있습니다. 앱 라우터는 서버 컴포넌트 및 스트리밍과 같은 React의 최신 기능을 사용할 수 있는 최신 라우터입니다.

Pages Router는 서버에서 렌더링된 React 애플리케이션을 구축할 수 있게 해 주고, 이전 Next.js 애플리케이션에 대해 계속 지원되는 최초의 Next.js 라우터입니다.

(사이드바 상단에는 앱 라우터와 페이지 라우터 기능 간에 전환할 수 있는 드롭다운 메뉴가 있습니다.각 디렉터리마다 고유한 기능이 있으므로 어떤 탭이 선택되었는지 추적하는 것이 중요합니다.)

페이지 상단의 이동 경로는 앱 라우터 문서를 보고 있는지 페이지 라우터 문서를 보고 있는지도 나타냅니다.



### Pre-Requisite Knowledge <a href="#pre-requisite-knowledge" id="pre-requisite-knowledge"></a>

(우리 문서는 초보자를 집중적으로 설계되었지만 문서가 Next.js 기능에 계속 집중할 수 있도록 기준선을 설정해야 합니다. 새로운 개념을 도입할 때마다 관련 문서에 대한 링크를 제공하도록 하겠습니다.)

문서를 최대한 활용하려면 HTML, CSS 및 React에 대한 기본적인 이해를 갖는 것이 좋습니다. React 기술을 배워야 한다면 기본 사항을 소개하는[ Next.js 기초 과정](https://nextjs.org/learn/foundations/about-nextjs)을 확인하세요.



### Accessibility

문서를 읽는 동안 스크린 리더를 사용할 때 최적의 접근성을 위해 Firefox 및 NVDA 또는 Safari 및 VoiceOver를 사용하는 것이 좋습니다.


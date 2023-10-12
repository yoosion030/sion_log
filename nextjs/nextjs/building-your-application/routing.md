# Routing

모든 애플리케이션의 뼈대는 라우팅입니다. 이 페이지에서는 웹 라우팅의 기본 개념과 Next.js에서 라우팅을 처리하는 방법을 소개합니다.



### Terminology

먼저, 문서 전체에서 이러한 용어가 사용되는 것을 볼 수 있습니다:

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

\- **Tree**: 계층 구조를 시각화하기 위한 규칙입니다. 예를 들어 상위 및 하위 컴포넌트가 있는 컴포넌트 트리, 폴더 구조 등이 있습니다.

\- **Subtree**: 새로운 루트(첫 번째)에서 시작하여 잎(마지막)에서 끝나는 나무의 일부입니다.

\- **Root**: 루트 레이아웃과 같은 트리 또는 하위 트리의 첫 번째 노드입니다.

\- **Leaf**: URL 경로의 마지막 세그먼트와 같이 자식이 없는 하위 트리의 노드입니다.

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

\- **URL Segment**: 슬래시로 구분된 URL 경로의 일부입니다.

\- **URL Path:** 도메인 뒤에 오는 URL의 일부(세그먼트로 구성)



### The `app` Router <a href="#the-app-router" id="the-app-router"></a>

버전 13에서 Next.js는 공유 레이아웃, 중첩 라우팅, 로딩 상태, 에러 헨들리 등을 지원하는 React Server 컴포넌트를 기반으로 구축된 새로운 앱 라우터를 도입했습니다.

앱 라우터는 `app`이라는 새 디렉터리에서 작동합니다. 앱 디렉터리는 페이지 디렉터리와 함께 작동하여 점진적인 채택을 허용합니다.

이를 통해 이전 동작에 대한 페이지 디렉터리에 다른 경로를 유지하면서 애플리케이션의 일부 경로를 새 동작으로 선택할 수 있습니다. 애플리케이션이 페이지 디렉터리를 사용하는 경우 페이지 라우터 설명서를 참조하세요.

{% hint style="info" %}
**Good to know**

앱 라우터는 페이지 라우터보다 우선순위가 높습니다. 디렉터리 간 경로는 동일한 URL 경로로 확인되어서는 안 되며 충돌을 방지하기 위해 빌드 타임에서 오류가 발생합니다.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

기본적으로 앱 내부의 컴포넌트는 React Server 컴포넌트입니다. 이는 성능 최적화이며 이를 쉽게 채택할 수 있으며 클라이언트 컴포넌트도 사용할 수 있습니다.



### Roles of Folders and Files <a href="#roles-of-folders-and-files" id="roles-of-folders-and-files"></a>

Next.js는 다음과 같은 파일 시스템 기반 라우터를 사용합니다:

\- **폴더**는 경로를 정의하는 데 사용됩니다. 경로는 root 폴더부터 `page.js` 파일이 포함된 최종 leaf 폴더까지 파일 시스템 계층 구조를 따라가는 중첩된 폴더의 단일 경로입니다.&#x20;

\- 파일은 경로 세그먼트에 표시되는 UI를 만드는 데 사용됩니다.



### Routes Segments

경로의 각 폴더는 경로 세그먼트를 나타냅니다. 각 경로 세그먼트는 URL 경로의 해당 세그먼트에 매핑됩니다.

<figure><img src="../../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Nested Routes

중첩된 경로를 만들려면 폴더를 서로 중첩하면 됩니다.&#x20;

예를 들어 앱 디렉터리에 두 개의 새 폴더를 중첩하여 새 `/dashboard/settings` 경로를 추가할 수 있습니다.

`/dashboard/settings` 경로는 세 개의 세그먼트로 구성됩니다.

\- `/` (Root segment)

\- `dashboard` (Segment)

\- `settings` (Leaf segment)



### File Conventions

Next.js는 중첩된 경로에서 특정 동작으로 UI를 생성하기 위한 특수 파일 세트를 제공합니다.

|                                                                                                         |                               |
| ------------------------------------------------------------------------------------------------------- | ----------------------------- |
| [`layout`](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#layouts)     | 세그먼트 및 해당 하위 항목에 대한 공유 UI     |
| [`page`](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#pages)         | 경로의 고유한 UI 및 경로에 공개적으로 액세스 가능 |
| [`loading`](https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming)     | 로드 UI를 위한 하위 세그먼트 및 하위 항목     |
| [`not-found`](https://nextjs.org/docs/app/api-reference/file-conventions/not-found)                     | 404 UI를 위한 하위 세그먼트 및 하위 항목    |
| [`error`](https://nextjs.org/docs/app/building-your-application/routing/error-handling)                 | 에러 UI를 위한 하위 세그먼트 및 하위 항목     |
| [`global-error`](https://nextjs.org/docs/app/building-your-application/routing/error-handling)          | 전역 에러 UI                      |
| [`route`](https://nextjs.org/docs/app/building-your-application/routing/route-handlers)                 | 서버 측 API 엔드포인트                |
| [`template`](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#templates) | 다시 렌더링된 레이아웃 UI               |
| [`default`](https://nextjs.org/docs/app/api-reference/file-conventions/default)                         | 병렬 경로에 대한 대체 UI               |



### Component Hierarchy (컴포넌트 계층)

경로 세그먼트의 특수 파일에 정의된 React 컴포넌트는 특정 계층 구조로 렌더링됩니다:



\- `layout.js`

\- `template.js`

\- `error.js` (React error boundary)

\- `loading.js` (React suspense boundary)

\- `not-found.js` (React error boundary)

\- `page.js` or 중첩된 `layout.js`![](<../../../.gitbook/assets/image (1) (1) (1) (1).png>)

중첩 경로에서는 세그먼트의 컴포넌트가 상위 세그먼트의 컴포넌트 내에 중첩됩니다.

<figure><img src="../../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>



### Colocation <a href="#colocation" id="colocation"></a>

특수 파일 외에도 앱 디렉터리의 폴더 내에 자체 파일(예: 컴포넌트, 스타일, 테스트 등)을 같은 위치에 배치할 수 있는 옵션이 있습니다.

이는 폴더가 경로를 정의하는 동안 `page.js` 또는 `Route.js`에서 반환된 콘텐츠만 공개적으로 주소를 지정할 수 있기 때문입니다.

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>



### Advanced Routing Patterns <a href="#advanced-routing-patterns" id="advanced-routing-patterns"></a>

앱 라우터는 또한 고급 라우팅 패턴을 구현하는 데 도움이 되는 일련의 규칙을 제공합니다:

\- 병렬 경로: 독립적으로 탐색할 수 있는 동일한 보기에 두 개 이상의 페이지를 동시에 표시할 수 있습니다. 자체 하위 탐색이 있는 분할 보기에 사용할 수 있습니다. 예: 대시보드.

\- 경로 차단: 경로를 가로채서 다른 경로에서 표시할 수 있습니다. 현재 페이지의 컨텍스트를 유지하는 것이 중요할 때 이를 사용할 수 있습니다.\
\
예: 하나의 작업을 편집하거나 피드에서 사진을 확장하는 동안 모든 작업을 볼 수 있습니다.

이러한 패턴을 사용하면 더 풍부하고 복잡한 UI를 구축할 수 있으며, 소규모 팀과 개별 개발자가 구현하기 복잡했던 기능을 통일할 수 있습니다.

# Pages and Layouts

Next.js 13 내부의 앱 라우터에는 페이지, 공유 layout 및 template을 쉽게 생성할 수 있는 새로운 파일 규칙이 도입되었습니다. 이 페이지는 Next.js 애플리케이션에서 이러한 특수 파일을 사용하는 방법을 안내합니다.



### Pages

페이지는 경로에 고유한 UI입니다.&#x20;

page.js 파일에서 컴포넌트를 내보내 페이지를 정의할 수 있습니다. 중첩된 폴더를 사용하여 경로를 정의하고 해당 경로에 공개적으로 액세스할 수 있도록 page.js 파일을 만듭니다.

앱 디렉터리 내에 page.js 파일을 추가하여 첫 번째 페이지를 만듭니다:

<figure><img src="../../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

```tsx
// `app/page.tsx` is the UI for the `/` URL
export default function Page() {
  return <h1>Hello, Home page!</h1>
}
```

```tsx
// `app/page.tsx` is the UI for the `/` URL
export default function Page() {
  return <h1>Hello, Home page!</h1>
}
```

{% hint style="info" %}
**Good to Know**

\- 페이지는 항상 경로 하위 트리의 리프입니다.&#x20;

\- .js, .jsx 또는 .tsx 파일 확장자를 페이지에 사용할 수 있습니다.&#x20;

\- 경로 세그먼트에 공개적으로 액세스할 수 있도록 하려면 page.js 파일이 필요합니다.

\- 페이지는 기본적으로 서버 컴포넌트이지만 클라이언트 컴포넌트로 설정할 수 있습니다.&#x20;

\- 페이지는 데이터 페칭을 할 수 있습니다.&#x20;
{% endhint %}



### Layouts

layout은 여러 페이지에서 공유되는 UI입니다. 탐색 시 레이아웃은 상태를 유지하고 대화형을 유지하며 다시 렌더링되지 않습니다. 레이아웃은 중첩될 수도 있습니다.

기본적으로 layout.js 파일에서 React 컴포넌트를 내보내는 방식으로 레이아웃을 정의할 수 있습니다. 컴포넌트는 렌더링 중에 하위 레이아웃(존재하는 경우) 또는 하위 페이지로 채워지는 하위 속성을 허용해야 합니다.



<figure><img src="../../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

```tsx
export default function DashboardLayout({
  children, // will be a page or nested layout
}: {
  children: React.ReactNode
}) {
  return (
    <section>
      {/* Include shared UI here e.g. a header or sidebar */}
      <nav></nav>
 
      {children}
    </section>
  )
}
```

{% hint style="info" %}
**Good to know:**

\- 최상위 레이아웃을 **루트 레이아웃**이라고 합니다. 루트 레이아웃은 애플리케이션의 모든 페이지에서 공유됩니다.&#x20;

\- 루트 레이아웃에는 html 및 body 태그가 포함되어야 합니다.

\- 모든 경로 세그먼트는 선택적으로 자체 레이아웃을 정의할 수 있습니다. 이러한 레이아웃은 해당 세그먼트의 모든 페이지에서 공유됩니다.

\- 경로의 레이아웃은 기본적으로 중첩됩니다. 각 상위 레이아웃은 React children prop을 사용하여 그 아래의 하위 레이아웃을 래핑합니다.

\- 라우트 그룹을 사용하여 공유 레이아웃 안팎에서 특정 경로 세그먼트를 선택할 수 있습니다.

\- 레이아웃은 기본적으로 서버 컴포넌트이지만 클라이언트 컴포넌트로 설정할 수 있습니다.

\- 레이아웃은 데이터 페칭을 할 수 있습니다.

\- 상위 레이아웃과 해당 하위 레이아웃 간에 데이터를 전달하는 것은 불가능합니다. 그러나 경로에서 동일한 데이터를 두 번 이상 가져올 수 있으며 React는 성능에 영향을 주지 않고 자동으로 요청의 중복을 제거합니다.

\- 레이아웃은 자체 아래의 경로 세그먼트에 접근할 수 없습니다. 모든 경로 세그먼트에 액세스하려면 클라이언트 컴포넌트에서 `useSelectedLayoutSegment` 또는 `useSelectedLayoutSegments`를 사용할 수 있습니다.

\- .js, .jsx 또는 .tsx 파일 확장자를 레이아웃에 사용할 수 있습니다.

\- layout.js와 page.js 파일은 동일한 폴더에 정의될 수 있습니다. 레이아웃이 페이지를 래핑합니다.
{% endhint %}



### Root Layout (Required)

폴더 내에 정의된 레이아웃(예: app/dashboard/layout.js)은 특정 경로 세그먼트(예: acme.com/dashboard)에 적용되고 해당 세그먼트가 활성화되면 렌더링됩니다. 기본적으로 파일 계층 구조의 레이아웃은 중첩되어 있습니다. 즉, children prop을 통해 하위 레이아웃을 래핑합니다.

<figure><img src="../../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

```tsx
export default function DashboardLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return <section>{children}</section>
}
```

{% hint style="danger" %}
루트 레이아웃에만 및 태그가 포함되어야 합니다.
{% endhint %}

위의 두 레이아웃을 결합하는 경우 루트 레이아웃(app/layout.js)은 대시보드 레이아웃(app/dashboard/layout.js)을 래핑하고, 이는 app/dashboard/\* 내부의 경로 세그먼트를 래핑합니다.

하위 레이아웃은 해당 내부의 경로 세그먼트만 래핑한다.

두 레이아웃은 다음과 같이 중첩됩니다:

<figure><img src="../../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

라우트 그룹을 사용하여 공유 레이아웃 안팎에서 특정 경로 세그먼트를 선택할 수 있습니다.



### Templates

템플릿은 각 하위 레이아웃이나 페이지를 래핑한다는 점에서 레이아웃과 유사합니다. 경로 전반에 걸쳐 지속되고 상태를 유지하는 레이아웃과 달리 템플릿은 탐색 시 각 하위 항목에 대해 새 인스턴스를 만듭니다.

이는 사용자가 템플릿을 공유하는 경로 사이를 탐색할 때 구성 요소의 새 인스턴스가 마운트되고 DOM 요소가 다시 생성되며 상태가 유지되지 않고 효과가 다시 동기화된다는 것을 의미합니다.

이러한 특정 동작이 필요한 경우가 있을 수 있으며 레이아웃보다 템플릿이 더 적합한 옵션입니다:

\- `useEffect`(예: 페이지 보기 로깅) 및 `useState`(예: 페이지별 피드백 양식)에 의존하는 기능입니다.

\- 기본 프레임워크 동작을 변경합니다. 예를 들어 레이아웃 내부의 정지 경계는 레이아웃이 처음 로드될 때만 fallback을 표시하고 페이지를 전환할 때는 표시하지 않습니다. 템플릿의 경우 각 navigation에 fallback가 표시됩니다.

template.js 파일에서 기본 React 컴포넌트를 내보내 템플릿을 정의할 수 있습니다. 컴포넌트는 `children` prop을 허용해야 합니다.

<figure><img src="../../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

```tsx
export default function Template({ children }: { children: React.ReactNode }) {
  return <div>{children}</div>
}
```

중첩 측면에서 template.js는 레이아웃과 해당 하위 항목(children) 사이에 렌더링됩니다:

```tsx
<Layout>
  {/* Note that the template is given a unique key. */}
  <Template key={routeParam}>{children}</Template>
</Layout>
```



### Modifiying \<head>

앱 디렉토리에서 내장된 SEO를 사용하여 제목 및 메타와 같은 HTML 요소를 수정할 수 있습니다.&#x20;

메타데이터는 레이아웃.js 또는 page.js 파일의 메타데이터 개체 또는 generateMetadata 함수를 내보내 정의할 수 있습니다.

```tsx
import { Metadata } from 'next'
 
export const metadata: Metadata = {
  title: 'Next.js',
}
 
export default function Page() {
  return '...'
}
```

{% hint style="info" %}
**Good to know**

\<title>및 \<meta>와 같은 \<head> 태그를 루트 레이아웃에 **수동으로 추가하면 안 됩니다.** 대신 \<head> 요소 스트리밍 및 중복 제거와 같은 고급 요구 사항을 자동으로 처리하는 메타데이터 API를 사용해야 합니다.
{% endhint %}




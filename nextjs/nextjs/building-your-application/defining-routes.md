# Defining Routes

이 페이지에서는 Next.js 애플리케이션에서 경로를 정의하고 구성하는 방법을 안내합니다.



### Creating Routes

Next.js는 폴더를 사용하여 경로를 정의하는 파일 시스템 기반 라우터를 사용합니다.

각 폴더는 URL 세그먼트에 매핑되는 경로 세그먼트를 나타냅니다. 중첩된 경로를 만들려면 폴더를 서로 중첩하면 됩니다.

<figure><img src="../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

특별한 page.js 파일은 경로 세그먼트에 공개적으로 액세스할 수 있도록 하는 데 사용됩니다.

<figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

이 예에서 `/dashboard/analytics URL` 경로에는 해당 page.js 파일이 없기 때문에 공개적으로 액세스할 수 없습니다. 이 폴더는 컴포넌트, 스타일시트, 이미지 또는 기타 같은 위치에 있는 파일을 저장하는 데 사용될 수 있습니다.



### Creating UI

각 경로 세그먼트에 대한 UI를 생성하는 데 특수 파일 규칙이 사용됩니다. 가장 일반적인 것은 경로에 고유한 UI를 표시하는 페이지와 여러 경로에서 공유되는 UI를 표시하는 layout입니다.

예를 들어 첫 번째 페이지를 만들려면 앱 디렉터리 내에 page.js 파일을 추가하고 React 컴포넌트를 내보냅니다.

{% code title="app/page.tsx" %}
```tsx
export default function Page() {
  return <h1>Hello, Next.js!</h1>
}
```
{% endcode %}








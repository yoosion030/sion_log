---
description: Next.js에서 지원하는 스타일링
---

# 스타일링

Next.js에서는 CSS Modules, Tailwind CSS, CSS-in-JS, Sass와 같은 스타일링 방식을 지원합니다. 가장 진입 장벽이 낮은 CSS Modules 방식에 대해 알아보겠습니다.



### CSS Modules

CSS Modules는 **CSS 클래스의 이름 중복 문제를 피할 수 있는 지역 스코프의 스타일링 방식**입니다. `.module.css` 확장자로 이름을 붙여 스타일을 정의하고 컴포넌트에서 가져와 사용할 수 있습니다.

{% code title="styles.module.css" %}
```css
.dashboard {
  padding: 24px;
}
```
{% endcode %}

{% code title="layout.tsx" %}
```tsx
import styles from './styles.module.css'
 
export default function DashboardLayout({
  children,
}) {
  return <section className={styles.dashboard}>{children}</section>
}
```
{% endcode %}



### 전역 스타일링

전역 스타일은 `app` 디렉토리 안에 있는 어떤 layout, page, component 파일에도 선언할 수 있습니다.

{% code title="app/global.css" %}
```css
body {
  padding: 20px 20px 60px;
  max-width: 680px;
  margin: 0 auto;
}
```
{% endcode %}

{% code title="app/layout.tsx" %}
```tsx
// 이렇게 적용된 스타일은 어플리케이션의 모든 경로에 적용됩니다.
import './global.css'
 
export default function RootLayout({
  children,
}) {
  return (
    <html>
      <body>{children}</body>
    </html>
  )
}
```
{% endcode %}

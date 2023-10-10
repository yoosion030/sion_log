---
description: 설치.
---

# Installation

시스템 요구 사항:

\- Node.js 16.14 이상.

\- macOS, Windows(WSL 포함) 및 Linux가 지원됩니다.



### Automatic Installation <a href="#automatic-installation" id="automatic-installation"></a>

모든 것을 자동으로 설정해주는 `create-next-app`을 사용하여 새로운 Next.js app을 시작하는 것이 좋습니다. 프로젝트를 만들려면 다음을 실행하세요:

<pre><code><strong>npx create-next-app@latest
</strong></code></pre>

설치 시 다음 메시지가 표시됩니다:

```
What is your project named? my-app
Would you like to use TypeScript? No / Yes
Would you like to use ESLint? No / Yes
Would you like to use Tailwind CSS? No / Yes
Would you like to use `src/` directory? No / Yes
Would you like to use App Router? (recommended) No / Yes
Would you like to customize the default import alias (@/*)? No / Yes
What import alias would you like configured? @/*
```

명령창이 표시되면 `create-next-app`은 프로젝트 이름으로 폴더를 생성하고 필요한 종속성을 설치합니다.

{% hint style="info" %}
**Good to know**

\- Next.js는 기본적으로 TypeScript, EsLint 및 TailwindCSS 구성과 함께 제공됩니다.

\- 선택적으로 프로젝트 루트의 src 디렉터리를 사용하여 애플리케이션 코드를 구성 파일에서 분리할 수 있습니다.
{% endhint %}

### Manual Installation <a href="#manual-installation" id="manual-installation"></a>

새 Next.js 앱을 수동으로 생성하려면 필수 패키지를 설치하세요:

```
npm install next@latest react@latest react-dom@latest
```

package.json 파일을 열고 다음 스크립트를 추가합니다:

```
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  }
}
```

이 스크립트는 애플리케이션 개발의 다양한 단계를 나타냅니다:

\- `dev`: `next dev`를 실행하여 개발 모드에서 Next.js를 시작합니다.

\- `build`: `next build`를 실행하여 프로덕션 용도로 애플리케이션을  빌드합니다.

\- `start`: `next start`를 실행하여 Next.js 프로덕션 서버를 시작합니다.

\- `lint`: `next lint`를 실행하여 Next.js의 내장 ESLint 구성을 설정합니다.



#### Creating directories

Next.js는 파일 시스템 기반 라우팅을 사용합니다. 즉, 파일 구조에 따라 애플리케이션의 경로가 결정됩니다.


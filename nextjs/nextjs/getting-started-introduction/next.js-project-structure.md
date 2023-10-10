# Next.js Project Structure

이 페이지는 Next.js 프로젝트의 파일 및 폴더 구조에 대한 개요를 제공합니다. `app` 및 `pages` 디렉터리 내의 최상위 파일 및 폴더, 구성 파일, 라우팅 규칙을 다룹니다.



### Top-level folders <a href="#top-level-folders" id="top-level-folders"></a>

| [`app`](https://nextjs.org/docs/app/building-your-application/routing)                     | 앱 라우터        |
| ------------------------------------------------------------------------------------------ | ------------ |
| [`pages`](https://nextjs.org/docs/pages/building-your-application/routing)                 | 페이지 라우터      |
| [`public`](https://nextjs.org/docs/app/building-your-application/optimizing/static-assets) | 정적 자산        |
| [`src`](https://nextjs.org/docs/app/building-your-application/configuring/src-directory)   | 애플리케이션 소스 폴더 |



### Top-level files <a href="#top-level-files" id="top-level-files"></a>

**Next.js**

|                                                                                                               |                           |
| ------------------------------------------------------------------------------------------------------------- | ------------------------- |
| [`next.config.js`](https://nextjs.org/docs/app/api-reference/next-config-js)                                  | Next.js 구성 파일             |
| [`package.json`](https://nextjs.org/docs/getting-started/installation#manual-installation)                    | 프로젝트 종속성 및 스크립트           |
| [`instrumentation.ts`](https://nextjs.org/docs/app/building-your-application/optimizing/instrumentation)      | OpenTelemetry 및 계측 파일     |
| [`middleware.ts`](https://nextjs.org/docs/app/building-your-application/routing/middleware)                   | Next.js 요청 미들웨어           |
| [`.env`](https://nextjs.org/docs/app/building-your-application/configuring/environment-variables)             | 환경 변수                     |
| [`.env.local`](https://nextjs.org/docs/app/building-your-application/configuring/environment-variables)       | 로컬 환경 변수                  |
| [`.env.production`](https://nextjs.org/docs/app/building-your-application/configuring/environment-variables)  | 프로덕션 환경 변수                |
| [`.env.development`](https://nextjs.org/docs/app/building-your-application/configuring/environment-variables) | 개발 환경 변수                  |
| [`.eslintrc.json`](https://nextjs.org/docs/app/building-your-application/configuring/eslint)                  | ESLint용 구성 파일             |
| `.gitignore`                                                                                                  | 무시할 Git 파일 및 폴더           |
| `next-env.d.ts`                                                                                               | Next.js용 TypeScript 선언 파일 |
| `tsconfig.json`                                                                                               | TypeScript용 구성 파일         |
| `jsconfig.json`                                                                                               | JavaScript용 구성 파일         |



## `app` Routing Conventions <a href="#app-routing-conventions" id="app-routing-conventions"></a>

### Routing Files

|                                                                                                   |                     |              |
| ------------------------------------------------------------------------------------------------- | ------------------- | ------------ |
| [`layout`](https://nextjs.org/docs/app/api-reference/file-conventions/layout)                     | `.js` `.jsx` `.tsx` | 레아아웃         |
| [`page`](https://nextjs.org/docs/app/api-reference/file-conventions/page)                         | `.js` `.jsx` `.tsx` | 페이지          |
| [`loading`](https://nextjs.org/docs/app/api-reference/file-conventions/loading)                   | `.js` `.jsx` `.tsx` | 로딩 UI        |
| [`not-found`](https://nextjs.org/docs/app/api-reference/file-conventions/not-found)               | `.js` `.jsx` `.tsx` | 404 페이지 UI   |
| [`error`](https://nextjs.org/docs/app/api-reference/file-conventions/error)                       | `.js` `.jsx` `.tsx` | 에러 UI        |
| [`global-error`](https://nextjs.org/docs/app/api-reference/file-conventions/error#global-errorjs) | `.js` `.jsx` `.tsx` | 전역 에러 UI     |
| [`route`](https://nextjs.org/docs/app/api-reference/file-conventions/route)                       | `.js` `.ts`         | API endpoint |
| [`template`](https://nextjs.org/docs/app/api-reference/file-conventions/template)                 | `.js` `.jsx` `.tsx` | 리렌더 레이아웃     |
| [`default`](https://nextjs.org/docs/app/api-reference/file-conventions/default)                   | `.js` `.jsx` `.tsx` | 병렬 경로 대체 페이지 |



### Nested Routes <a href="#nested-routes" id="nested-routes"></a>

| [`folder`](https://nextjs.org/docs/app/building-your-application/routing#route-segments)       | Route segment    |
| ---------------------------------------------------------------------------------------------- | ---------------- |
| [`folder/folder`](https://nextjs.org/docs/app/building-your-application/routing#nested-routes) | 중첩 route segment |



### Dynamic Route

| [`[folder]`](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes#convention)                       | 동적 route segment     |
| --------------------------------------------------------------------------------------------------------------------------- | -------------------- |
| [`[...folder]`](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes#catch-all-segments)            | 포괄 route segment     |
| [`[[...folder]]`](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes#optional-catch-all-segments) | 선택적 포괄 route segment |



### Route Groups and Private Folders(경로 그룹 및 개인 폴더)

| [`(folder)`](https://nextjs.org/docs/app/building-your-application/routing/route-groups#convention)   | 라우팅에 영향을 주지 않는 그룹 경로   |
| ----------------------------------------------------------------------------------------------------- | ---------------------- |
| [`_folder`](https://nextjs.org/docs/app/building-your-application/routing/colocation#private-folders) | 라우팅에서 폴더 및 모든 하위 경로 선택 |



### Parallel and Intercepted Routes(평행 및 차단 경로)

| [`@folder`](https://nextjs.org/docs/app/building-your-application/routing/parallel-routes#convention)            | 명명된 슬롯        |
| ---------------------------------------------------------------------------------------------------------------- | ------------- |
| [`(.)folder`](https://nextjs.org/docs/app/building-your-application/routing/intercepting-routes#convention)      | 같은 레벨을 가로챔    |
| [`(..)folder`](https://nextjs.org/docs/app/building-your-application/routing/intercepting-routes#convention)     | 한 레벨 위에서 가로채기 |
| [`(..)(..)folder`](https://nextjs.org/docs/app/building-your-application/routing/intercepting-routes#convention) | 두 레벨 위에서 가로채기 |
| [`(...)folder`](https://nextjs.org/docs/app/building-your-application/routing/intercepting-routes#convention)    | 루트에서 가로채기     |



### Metadata File Conventions

**App Icons**

| [`favicon`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata/app-icons#favicon)                                | `.ico`                              | 파비콘 파일          |
| --------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- | --------------- |
| [`icon`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata/app-icons#icon)                                      | `.ico` `.jpg` `.jpeg` `.png` `.svg` | 앱 아이콘 파일        |
| [`icon`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata/app-icons#generate-icons-using-code-js-ts-tsx)       | `.js` `.ts` `.tsx`                  | 생성된 앱 아이콘       |
| [`apple-icon`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata/app-icons#apple-icon)                          | `.jpg` `.jpeg`, `.png`              | Apple 앱 아이콘 파일  |
| [`apple-icon`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata/app-icons#generate-icons-using-code-js-ts-tsx) | `.js` `.ts` `.tsx`                  | 생성된 Apple 앱 아이콘 |



**Open Graph and Twitter Images**

|                                                                                                                                               |                              |                  |
| --------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------- | ---------------- |
| [`opengraph-image`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata/opengraph-image#opengraph-image)                      | `.jpg` `.jpeg` `.png` `.gif` | 오픈 그래프 이미지 파일 열기 |
| [`opengraph-image`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata/opengraph-image#generate-images-using-code-js-ts-tsx) | `.js` `.ts` `.tsx`           | 생성된 오픈 그래프 이미지   |
| [`twitter-image`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata/opengraph-image#twitter-image)                          | `.jpg` `.jpeg` `.png` `.gif` | 트위터 이미지 파일       |
| [`twitter-image`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata/opengraph-image#generate-images-using-code-js-ts-tsx)   | `.js` `.ts` `.tsx`           | 생성된 트위터 이미지      |

\
**SEO**

|                                                                                                               |             |              |
| ------------------------------------------------------------------------------------------------------------- | ----------- | ------------ |
| [`sitemap`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata/sitemap#static-sitemapxml)    | `.xml`      | Sitemap file |
| [`sitemap`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata/sitemap#generate-a-sitemap)   | `.js` `.ts` | 생성된 사이트맵     |
| [`robots`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata/robots#static-robotstxt)       | `.txt`      | Robots file  |
| [`robots`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata/robots#generate-a-robots-file) | `.js` `.ts` | 생성된 로봇 파일    |



### `pages` Routing Conventions <a href="#pages-routing-conventions" id="pages-routing-conventions"></a>

### Special Files

| [`_app`](https://nextjs.org/docs/pages/building-your-application/routing/custom-app)                                          | `.js` `.jsx` `.tsx` | Custom App        |
| ----------------------------------------------------------------------------------------------------------------------------- | ------------------- | ----------------- |
| [`_document`](https://nextjs.org/docs/pages/building-your-application/routing/custom-document)                                | `.js` `.jsx` `.tsx` | Custom Document   |
| [`_error`](https://nextjs.org/docs/pages/building-your-application/routing/custom-error#more-advanced-error-page-customizing) | `.js` `.jsx` `.tsx` | Custom Error Page |
| [`404`](https://nextjs.org/docs/pages/building-your-application/routing/custom-error#404-page)                                | `.js` `.jsx` `.tsx` | 404 Error Page    |
| [`500`](https://nextjs.org/docs/pages/building-your-application/routing/custom-error#500-page)                                | `.js` `.jsx` `.tsx` | 500 Error Page    |

### Routes

**Folder convention**

| [`index`](https://nextjs.org/docs/pages/building-your-application/routing/pages-and-layouts#index-routes)        | `.js` `.jsx` `.tsx` | Home page |
| ---------------------------------------------------------------------------------------------------------------- | ------------------- | --------- |
| [`folder/index`](https://nextjs.org/docs/pages/building-your-application/routing/pages-and-layouts#index-routes) | `.js` `.jsx` `.tsx` | 중첩된 page  |

**File convention**

| [`index`](https://nextjs.org/docs/pages/building-your-application/routing/pages-and-layouts#index-routes) | `.js` `.jsx` `.tsx` | Home page |
| --------------------------------------------------------------------------------------------------------- | ------------------- | --------- |
| [`file`](https://nextjs.org/docs/pages/building-your-application/routing/pages-and-layouts)               | `.js` `.jsx` `.tsx` | 중첩된 page  |



### Dynamic Routes

**Folder convention**

| [`[folder]/index`](https://nextjs.org/docs/pages/building-your-application/routing/dynamic-routes)                                  | `.js` `.jsx` `.tsx` | Dynamic route segment            |
| ----------------------------------------------------------------------------------------------------------------------------------- | ------------------- | -------------------------------- |
| [`[...folder]/index`](https://nextjs.org/docs/pages/building-your-application/routing/dynamic-routes#catch-all-segments)            | `.js` `.jsx` `.tsx` | Catch-all route segment          |
| [`[[...folder]]/index`](https://nextjs.org/docs/pages/building-your-application/routing/dynamic-routes#optional-catch-all-segments) | `.js` `.jsx` `.tsx` | Optional catch-all route segment |



**File convention**

| [`[file]`](https://nextjs.org/docs/pages/building-your-application/routing/dynamic-routes)                                  | `.js` `.jsx` `.tsx` |  동적 route segment    |
| --------------------------------------------------------------------------------------------------------------------------- | ------------------- | -------------------- |
| [`[...file]`](https://nextjs.org/docs/pages/building-your-application/routing/dynamic-routes#catch-all-segments)            | `.js` `.jsx` `.tsx` | 포괄 route segment     |
| [`[[...file]]`](https://nextjs.org/docs/pages/building-your-application/routing/dynamic-routes#optional-catch-all-segments) | `.js` `.jsx` `.tsx` | 선택적 포괄 route segment |


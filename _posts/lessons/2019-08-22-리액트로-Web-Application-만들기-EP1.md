---
layout: post
category: lessons
tagline: "리액트로 Web Application 만들기 EP1"
tags: [react, frontend, webDev, dev, programming]
img: react_lesson/webAppImg.png
img-mobile:
img2:
img3:
author: hwansDev
title2: Improve the desing of your blog
title3: Make it a full of slides
css:
js:
bgcolor: ff5a71
keywords: helium, web desing, css, html, bootstrap 4
canonical: https://hwansdev.github.io/
---

{% include JB/setup %}

## 리액트로 Web Application 만들기

<br>

<!--more-->

React.js 혹은 Vue.js 혹은 Angular.js를 활용하여 SPA를 개발해본 자<br>
React.js + Redux를 가지고 웹 어플리케이션을 개발해본 자<br>
React.js + Next.js에 대한 개발경험이 있는 자..<br>

Web FrontEnd 채용 공고를 보면 흔히들 볼수 있는 요건들입니다.<br>
특히 특정 프레임워크를 활용하여 개발하는 것을 선호함을 볼수 있는데요.<br>

<br>

<img src="https://existek-838c.kxcdn.com/wp-content/uploads/2019/03/top-front-end-frameworks-in-2019-graph-1800x751.png" width="500px" height="300px">

<br>

그 중에서도 뜨거운 인기를 자랑하는 <b>React.js</b><br>
이 React.js를 가지고 Web Application을 같이 개발해보는 경험을 해보고자 합니다.<br>
저희가 만들 Web Applicatoin은 OP.GG와 같은 게임 전적을 확인하는 사이트입니다.<br>

<br>

##### React.js를 모르는 분들을 위한 소개

React.js는 Facebook에서 만든 모던 프론트엔드 개발을 위한 라이브러리로,<br>
UI의 개발 및 복잡도를 컨트롤하기 위해 개발되어졌으며,<br>
현재 많은 프론트엔드 개발자들의 사랑을 받으며 꾸준히 성장중입니다.<br>
(2019-08-22 현재 Latest Version: 16.9.0)<br>

React를 알면 React-Native를 사용하여, 앱 개발도 할 수 있고,<br>
Proton-Native를 이용하여, 데스크탑 앱을 개발할 수 있습니다.<br>
(추상화가 잘되어있어, 타 플랫폼에서도 사용가능 하기 때문에 이러한 장점을 누릴 수 있습니다.)<br>

<br>

### 개발을 하기 위한 환경구성

<br>
개발을 하기 위한 환경 구성을 해볼건데요!<br>
먼저 필요한 것들이 있습니다!<br>
<br>

1. `Text-Editor (VScode, Atom...) 설치`
2. `Node.js 설치`
3. `Homebrew && Yarn 설치 (MacOS 사용자의 경우)`

일단 요 3가지가 설치되어야 저와 같이 개발환경 구성을 할 수 있는데요!<br>
간단히 설명드리면, Text-Editor란 코드를 좀 더 편안하고 생산성있게 작성할 수 있도록 도와주는 프로그램입니다.<br>
Atom과 Vscode, Bracket등.. 다양한 에디터들이 있으며, 개인적으로는 VScode를 추천드립니다.<br>

1번이 설치가 끝났으면, Node.js를 설치해야하는데요!<br>
리액트를 설치하고 리액트 관련 외부 패키지를 사용하기 위해서 NPM(Node Package Manager)이 필요한데<br>
NPM은 Node.js를 설치해야 사용가능하기에 Node.js를 설치합니다.<br>
<a href="https://nodejs.org/ko/">여기</a>를 누르시면 다운로드 사이트로 이동합니다.<br>
설치후 잘되었는지 확인하기 위해서는 터미널을 여시고 아래 명령어를 입력하여 확인이 가능합니다.

```
# node.js 버젼확인 : ex) v12.6.0
node -version

# npm 버젼확인 : ex) 6.10.3
npm -version
```

2번까지 끝이난다면 React.js로 개발하기 위한 준비는 끝이납니다.<br>
하지만 MacOS를 사용하시는 분들은 Homebrew와 Yarn을 설치를 하도록 하겠습니다.<br>
Homebrew는 Apple(또는 Linux 시스템)에서 제공하지 않는 유용한 패키지 관리자입니다.<br>
Homebrew를 설치하는 이유는 Yarn을 설치하기 위함입니다.<br>
NPM을 이용하여 리액트 관련 외부 패키지를 설치할 때 이슈가 생기는 경우가 간혹있는데<br>
이런 경우 Yarn을 사용하는 것을 권장드립니다.<br>
Yarn은 React.js를 개발한 Facebook에서 만든 자바스크립트 패키지 매니저로,<br>
NPM보다 속도 측면에서 빠르다는 장점이 있습니다.<br>
하단의 코드를 복사하여 터미널에 붙여넣기 후 엔터를 누르시면 설치가 됩니다.<br>

```
# Homebrew 설치
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

# 설치 후 버젼확인
brew --version

# Yarn 설치
brew install yarn

# 설치 후 버젼확인
yarn --version
```

<br>

### React.js 개발환경세팅

<br>

개발을 위한 환경을 갖추었으니 드디어 React.js 개발을 위한 개발환경을 갖춰보도록 하겠습니다.<br>
React.js를 개발환경을 갖추는 방법으로는 2가지가 있는데요!<br>

(1) CRA(create-react-app)을 이용한 개발환경세팅<br>
(2) 직접 개발환경세팅<br>

1번의 경우 위에서 했던 것처럼 해당 명령어(`yarn global add create-react-app`)를 터미널에 입력하여 설치한 후,<br>
`creact-react-app ${projectName}`를 터미널에 입력하면 projectName으로 react 프로젝트를 간편히 만들어줍니다.<br>
굉장히 편리하지만, 쓰지않는 것들과 어떻게 작동하는지 모르는 요소들이 많이 있어서 가급적 사용하지 않는데,<br>
리액트에 경험이 없는 경우 혹은 빠르게 프로토타이핑을 개발하는 경우에는 사용해도 좋을 것 같습니다.<br>

2번의 경우 1번과 달리 일일히 설치하고 만들어줘야하는 조금의 불편함이 있긴하지만,<br>
직접 쓸 것들만 설치하고, 개발환경을 100% 본인이 제어하기에 나중에 문제가 생겼을 때도<br>
금방 해결할 수 있고, 여러부분의 장점이 있습니다.<br>
저희 프로젝트는 조금 까다롭지만 추후의 더 큰 편리함을 위해 직접 개발환경을 세팅할 것입니다.<br>

<br>

`1. mkdir ${projectName}`

터미널을 켜고 해당 명령어를 입력하여 프로젝트를 관리할 폴더를 만듭니다.<br>
제 경우에는 `mkdir React_OP_GG`로 하였습니다.<br>
<br>

`2. package.json 생성 (npm init)`

터미널을 통해 해당 폴더(`cd ${projectName}`)에 들어가서 `npm init -y`이라는 명령어를 입력합니다.<br>
npm init이라는 명령어는 package.json이라는 프로젝트 정보를 담은 json파일을 만들어줍니다.<br>
npm init을 하면 각각의 항목에 무엇이 들어갈지 물어보는데 npm init -y를 하면<br>
모든 요소에 대해 default값을 넣어 만들어줍니다.<br>

`3. package.json 정보 수정`

텍스트 에디터를 켜서 해당 프로젝트 폴더에 들어가면 package.json이라는 파일이 존재하는 것이 보이실텐데요!<br>
package.json은 지금 default값을 넣어 만들어진 상태이기 때문에 저희의 프로젝트 정보에 맞게 수정해줍니다.<br>
아래는 제가 미리 수정한 package.json입니다.<br>

```json
{
  "name": "${yourProjectName}",
  "version": "1.0.0",
  "description": "Opgg site to make with react.js",
  "main": "index.js",
  // 명령어를 일일히 입력하지 않아도 이렇게 정리해놓으면
  // yarn run dev하면 parcel src/index.html가 실행됩니다.
  // 개발시 생산성 향상에 도움이 됩니다.
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "parcel src/index.html",
    "build": "parcel build src/index.html"
  },
  "author": "",
  "license": "ISC",
  // 이 해당 옵션은 browserslist 라이브러리에 대한 옵션으로서,
  // 서로 다른 front-end 툴 간에 브라우저의 타겟을 공유하기 위해 사용합니다.
  // 다음과 같은 곳에서 사용되며, 지정하는 값을 하단의 모듈들이 참고합니다.

  // Autoprefixer
  // babel-preset-env
  // postcss-preset-env
  // eslint-plugin-compat
  // stylelint-no-unsupported-browser-features
  // postcss-normalize

  // IE 10과 99.5% 정도의 커버리지를 갖는 인기있는 브라우저를 지원하겠다라는 의미
  "browserslist": ["cover 99.5%", "IE 10"],
  // 개발단에서 사용할 모듈
  "devDependencies": {
    "@babel/core": "^7.5.5",
    "@babel/preset-react": "^7.0.0",
    "babel-preset-es2015": "^6.24.1",
    "parcel-bundler": "^1.12.3"
  },
  // 실제 배포할 서비스에서 사용할 모듈
  "dependencies": {
    "aix": "0.0.15",
    "autoprefixer": "^9.6.1",
    "axios": "^0.19.0",
    "babel-polyfill": "^6.26.0",
    "postcss-modules": "^1.4.1",
    "react": "^16.8.6",
    "react-dom": "^16.8.6",
    "react-redux": "^7.1.0",
    "redux": "^4.0.4",
    "redux-devtools-extension": "^2.13.8",
    "regenerator-runtime": "^0.13.3",
    "styled-components": "^4.3.2"
  }
}
```

package.json에서 중요한 것은 devDependencies와 dependencies인데요.<br>
devDependencies는 개발환경에서 사용할 모듈을 의미하며,<br>
dependencies는 나중에 유저에게 제공할 프로덕트에 필요한 모듈을 의미합니다.<br>

devDependencies에서는 눈여겨볼 것이 babel과 parcel이 있네요!<br>
babel은 자바스크립트 컴파일러로, 입력과 출력 모두 자바스크립트입니다.<br>
최신 문법의 자바스크립트를 구버젼의 자바스크립트로 문법을 변환시켜주어<br>
브라우저들이 문제없이 코드를 인식하도록 도와줍니다.<br>
저희 또한 ES2015(ES6) 문법을 사용할 것이기에, babel 설치가 필요합니다.<br>

parcel은 필요한 의존성(dependencies)에 대해 정확하게 추적하여 해당하는 의존성들을 그룹핑해주는 도구입니다.<br>
webpack, rollup과 같은 다른 번들러도 있지만, 앞선 번들러와 달리 별도의 설정이 필요없고,<br>
워커 프로세스를 이용하여 멀티코어 컴파일을 하며, 파일 시스템 캐시를 갖고 있어 재시작후에도 빠른 리빌드를 제공해줍니다.<br>
parcel의 장점만 너무 설명드렸는데, 코드 스플리팅과 같은 작업에서는 또 다른 번들러보다 느려서<br>
<a href="https://medium.com/js-imaginea/comparing-bundlers-webpack-rollup-parcel-f8f5dc609cfd">정확한 비교를 해놓은 글</a>을 공유드릴테니 읽어보시고 맞는 번들러를 사용하시는 걸 추천드립니다.<br>
해당 프로젝트 튜토리얼에서는 파셀을 쓸 예정입니다. 다른 번들러를 설정하여 사용하셔도 괜찮습니다.<br>

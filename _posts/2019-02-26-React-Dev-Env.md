---
layout: post
title:  "React.js 시작하기"
subtitle:   "React 환경설정"
categories: devlog
tags: react 리액트 환경설정
---

# 리액트가 뭐죠?

[React.js](https://reactjs.org/)는 웹 개발용 javascript 라이브러리다.
이게 뭐냐고 물어보면 그냥 웹 화면을 쉽게 개발할 수 있게 도와주는 거라고 말하고 싶다.
Spring으로 웹 개발을 해봤다면 [Java](https://www.java.com/ko/), [Apache Tomcat](http://tomcat.apache.org/) 가 익숙하겠지? 
React.js 에서는 [JavaScript](https://www.javascript.com/), [Node.js](https://nodejs.org/ko/) 가 그 역할을 대신한다고 볼 수 있다.

좀 더 개념을 정리해보자면 Spring이나 React.js 는 웹 페이지를 개발을 쉽게 도와주는 Framework 이다.
Java나 JavaScript는 개발 언어가 되겠고, Apache Tomcat과 Node.js 는 엄밀히 말하면 좀 다를 수 있겠지만 서버를 띄워주는 역할을 한다.
이를 간단히 표로 비교해보면 아래와 같다.


|Framework|Spring|React.js|
| :---: | :---: | :---: |
|Language|Java|JavaScript|
|Server Side|Apache Tomcat(Apache Maven)|Node.js(npm)|


Spring은 우리나라가 유난히 Java를 많이 쓰는 곳이라 아직도 많은 곳에서 쓴다. 하나의 페이지를 추가 개발하려면 Controller, Service, ServiceImpl, DAO 등등 거의 하나씩 새로 또 만들어줘야했다. 보통 Spring으로 개발할 경우에는 Dependency가 필요한 데, 이를 Maven을 통해서 관리되도록 했다. 이 때, Java등 버전을 또 제대로 못 맞추면 빌드하기가 힘들었다. Spring에서도 위와 같은 문제 때문에 Spring Boot로 좀 더 쉽게 개발할 수 있도록 지원하고 있다.

React.js는 facebook에서 밀고 있는 framework이다. Spring Boot처럼 쉽게 리액트 개발을 시작하기 위해서는 facebook에서 제공하는 [create-react-app](https://github.com/facebook/create-react-app)을 이용하면 된다. 우선 [create-react-app](https://github.com/facebook/create-react-app) 으로 이동해서 README.md 파일을 한 번 보자. [Creating an App](https://github.com/facebook/create-react-app#creating-an-app) 여기 밑으로 개발 환경을 어떻게 맞추면 될 지도 상세히 적어두었다. 나같이 어줍잖은 블로그보다 이런 **공식 깃헙을 보는게 개발 환경을 정할 때는 중요**하다. (보니까 내가 쓰던 npm도 버전이 올라가면서 npx로 쓸 수 있게 변경이 되었나보다)

# 개발 환경

  1. [Node.js설치](https://nodejs.org/ko/download/)(최신 LTS 버전: 10.15.1 (includes npm 6.4.1))
  2. [Visual Studio Code](https://code.visualstudio.com/)(자바스크립트 개발툴;구글에서 VSC로 검색하면 편함)
  3. [Yarn](https://yarnpkg.com/lang/en/)(Stable: v1.13.0; 굳이 없어도 되지만 하는 김에 같이 해보자 )

설치는 그냥 다운로드 받고 실행-Next-Finish 만 하면 된다.(자동으로 PATH 등록이 될 것이다)

# 실행하기

이제 Node.js를 이용해서 create-react-app을 가져올 것이다. 개발환경을 위와 동일하게 맞췄다면 터미널을 열어서 아래의 명령을 실행하자.

##### 음..터미널이 뭐에요? 터미널 중에 뭘 해야하죠?
  1. ```윈도우 키-모든 프로그램```을 눌러보면 ```Node.js```가 보일 것이다. ```Node.js command prompt``` 를 실행하자.
  2. 윈도우 키-프로그램 및 파일 검색-```cmd``` 입력
  3. VSC 에서 ``` Ctrl+` ``` 을 누르면 터미널이 열린다.

### npx
```
npx create-react-app my-app
```

실행이 잘 된다. 나는 Yarn도 미리 설치가 되어 있어서 그런지 yarn 명령어를 추천해준다.

```
cd my-app
yarn start
```

이렇게하니 바로  http://localhost:3000/ 가 띄워지고 거기서 리액트 로고가 열심히 돌고 있다. 이러면 **리액트 환경설정이 끝났다**. 이제 js나 css를 수정하면 나만의 웹 페이지를 개발할 수 있게 된다. Yarn이 설치가 안되어 있는 경우는 어떻게 뜨는 지 확인하기가 좀 귀찮으니 Node.js 에서 Yarn 설치하는 방법만 추가로 작성하겠다.

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- default -->
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-3014668630648493"
     data-ad-slot="3073032858"
     data-ad-format="auto"
     data-full-width-responsive="true"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>
##### Node.js 에서 Yarn 설치하기

```
npm install yarn
```

여기서 -g 옵션을 줘서 글로벌하게 쓸 수 있게 할 수도 있는데, 글로벌을 남용하면 이상하게 꼬일 수 있으니 조심하자. Node.js 명령어들에 대해서는 다음에 한 번 정리해야겠다. 이상 끝.

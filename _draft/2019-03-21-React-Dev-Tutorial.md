---
layout: post
title:  "React.js Tutorial Tic Tac Toe"
subtitle:   "리액트 공식 튜토리얼 tic tac toe 만들기"
categories: devlog
tags: react 리액트 tutorial 튜토리얼 
---

# 리액트 공식 튜토리얼

[리액트 공식 홈페이지](https://reactjs.org/)를 가보면 [튜토리얼](https://reactjs.org/tutorial/tutorial.html)을 제공하고 있다.
공식 홈페이지에서 한글 언어를 지원하길래 튜토리얼을 의미하는 [자습서](https://ko.reactjs.org/tutorial/tutorial.html)를 눌러보니
여긴 뭐 그대로 **영어**라 사람들이 편히 이해할 수 있도록 포스팅을 해보기로 했다.
튜토리얼은 **tic tac toe** 라고 불리는 게임을 만들어보는 내용이다. 굳이 번역을 해보자면 삼목(?)이라고 할 수 있겠다.
([크롬을 열고 tic tac toe 를 검색](https://www.google.com/search?ei=uS6TXPCcBIyi8AXcgpUQ&q=tic+tac+toe&oq=tic+tac+toe&gs_l=psy-ab.3..0i71l8.0.0..264664...0.0..0.0.0.......0......gws-wiz.W1qDJBD2_p8)
해보면 바로 tic tac toe 게임을 즐겨볼 수도 있다.)
링크를 보면 알겠지만 전체적으로 JSX나 Babel, ES6 등 **문법적 내용**도 있고 Component, props, state와 같은 **리액트 개발에 필수적인 내용**도 있다.
그래서 적지 않은 양이기 때문에 이 포스팅으로 편히 따라가길 바란다. 구성도 원본과 동일하게 하였다.
(공식 홈페이지에 튜토리얼 한국어 버전을 contribute 할 수 있을까?)

## 튜토리얼 섹션

튜토리얼은 아래와 같이 구성되어 있다고한다.

- Setup for the Tutorial will give you a **starting point** to follow the tutorial.
- Overview will teach you **the fundamentals** of React: components, props, and state.
- Completing the Game will teach you the **most common techniques** in React development.
- Adding Time Travel will give you a **deeper insight** into the unique strengths of React.

한글로 표현하자면,

- [튜토리얼 환경설정](##-튜토리얼-환경설정)은 **어떻게 리액트를 시작할 지** 알려줄 것이다.
- [개요](##-개요)에서는 **리액트의 기본**인 **Components, props, state**에 대해 알려줄 것이다.
- [게임 완성하기]()에서는 **리액트 개발에서 자주 쓰이는 기술**들에 대해 배울 수 있다.
- [시간 여행 추가하기]()에서는 **리액트만의 강점**에 대해 더 깊게 이해할 수 있다.

### 그래서 우리가 만드는 게 뭐죠?

[결과물](https://codepen.io/gaearon/pen/gWWZgR?editors=0010)은 [CodePen](https://codepen.io/) 이라고 하는 곳에 올려져 있다.
CodePen은 굳이 환경설정을 하지 않아도 웹 상에서 쉽게 코딩해보고 결과물을 확인 할 수 있게 도와주는 곳이라고 보면 되겠다.

### 필요한 선행 지식

튜토리얼은 HTML, JavaScript에 대해 기본적으로 알고 있다고 생각하고 만들어졌다.
사실 그렇게 어려운 건 없어서 아무 언어로 프로그래밍을 해봤다면 쉽게 따라할 수 있을 것이다.
그리고 ES6(Babel)에서 추가된 let, const, arrow function과 관련된 내용도 있기 때문에 모른다면 
[가이드](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)를 참고하기 바란다.

## 튜토리얼 환경설정

**두 가지 방식**이 있는데, 하나는 앞서 말한 **CodePen**에서 진행하는 방법, 하나는 **로컬**에서 진행하는 방법이다.
로컬에서 진행하려면 Visual Studio Code와 같은 에디터, Node.js 설치가 필요한데, 이건 기존에 작성한 나의 포스트로 대체하겠다.
로컬에서 진행하는 것은 [코딩 시작하기](###-코딩-시작하기)에서 더 자세히 쓰겠다.

  1. [CodePen으로 웹에서 시작하기](https://codepen.io/gaearon/pen/oWWQNa?editors=0010)
  2. [로컬에서 시작하기](https://jmhmunhwan.github.io/devlog/2019/02/26/React-Dev-Env/)
  
## 개요

환경설정이 다 끝났으면 이제 본격적으로 시작해보자. **개요**에서는 대략적으로 리액트와 리액트 문법에 대해서 작성되었다.

### 리액트가 뭐죠?

리액트는 유저 인터페이스를 만들어주는 JavaScript 라이브러리다. 리액트는 components 라고 불리는 각각의 조각을 붙여 화면을 만들게 도와준다.
리액트는 여러 컴포넌트 종류가 있는데, `React.Component` 로 설명을 하려고 한다.

```javascript
class ShoppingList extends React.Component {
  render() {
    return (
      <div className="shopping-list">
        <h1>Shopping List for {this.props.name}</h1>
        <ul>
          <li>Instagram</li>
          <li>WhatsApp</li>
          <li>Oculus</li>
        </ul>
      </div>
    );
  }
}

// Example usage: <ShoppingList name="Mark" />
```

리액트는 컴포넌트를 통해 화면을 구성하게 되는데, 데이터가 바뀔 때 `state`와 `props`(properties의 준말)를 통하면
리액트가 알아서 효율적으로 데이터를 업데이트하여 화면에 다시 보여주게 된다.
`render` 메소드(method)는 return 에 화면에 보여줄 것을 담게 되는데, 리액트에서는 **React element**가 된다.
이것을 앞서 작성한 JSX 방식으로도 할 수 있고, 아래와 같이 React API 를 이용할 수도 있다.(보통 **JSX를 추천!**)

```javascript
return React.createElement('div', {className: 'shopping-list'},
  React.createElement('h1', /* ... h1 children ... */),
  React.createElement('ul', /* ... ul children ... */)
);
```

### 코딩 시작하기

[튜토리얼 환경설정](##-튜토리얼-환경설정)에서 1.CodePen으로 시작한 경우에는 
[여기](https://codepen.io/gaearon/pen/oWWQNa?editors=0010)를 눌러 시작하면 된다.
2. 로컬에서 시작한 경우에는 VSC에서 프로젝트 폴더를 열어서 시작하자.
CSS를 공부할 건 아니라서 CSS는 튜토리얼에서 제공해주는 그대로 사용하자.

<details>

<summary><b>로컬에서 환경설정하기</b></summary>


1. [Node.js 최신버전 설치](https://nodejs.org/en/)
2. 프로젝트 폴더를 구성할 위치에서 아래 명령어 실행

```bash
npx create-react-app my-app
```

3.  `src/` 폴더 아래에 있는 파일들 전체 삭제(src 폴더 자체는 남겨두자). 아래 명령어를 순서대로 실행해도 된다.

```bash
cd my-app
cd src

# Mac / Linux:
rm -f *

# Windows:
del *

# 프로젝트 폴더로 복귀
cd ..
```

4. [CSS code](https://codepen.io/gaearon/pen/oWWQNa?editors=0100)를 복사해서 `src/index.css` 에 저장

5. [JS code](https://codepen.io/gaearon/pen/oWWQNa?editors=0010)를 복사해서 `src/index.js` 에 저장

6. `src/index.js`에 아래의 3줄 추가하기:

```js
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
```

그러면 프로젝트 폴더에서 `npm start` 명령을 통해 실행이 가능하다. 실행 후, `http://localhost:3000` 에서 3x3의 사각형들이 보이면 끝.

![완료 화면](https://ko.reactjs.org/static/tictac-empty-1566a4f8490d6b4b1ed36cd2c11fe4b6-a9336.png)

</details>

코드들을 살펴보면, 튜토리얼은 3개의 컴포넌트로 구성되어 있다.

- Square
- Board
- Game

Square 컴포넌트에는 하나의 `<button>` 태그가 있고, Board 컴포넌트를 분석해보면 9개의 Square 컴포넌트가 들어간다.
우리는 `/* TODO */`와 `/* status */`를 채워서 게임을 완성시키자.

### props를 통해 데이터 전달하기

튜토리얼에서는 복사/붙여넣기를 하지말고 직접 타이핑하는 것이 개발 실력 향상에 도움이 될 거라고 한다.

우선, `Board` class의 `renderSquare` 메소드를 다음 내용으로 바꾸자:

```javascript
class Board extends React.Component {
  renderSquare(i) {
    return <Square value={i} />;
  }
```

`Sqaure`의 `render` 메소드에서 `/* TODO */` 를 `{this.props.value}` 로 바꾸자;

```javascript
class Square extends React.Component {
  render() {
    return (
      <button className="square">
        {this.props.value}
      </button>
    );
  }
}
```


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
(튜토리얼 한글화 작업 중이긴 하다 https://reactjs-org-ko.netlify.com/tutorial/tutorial.html)

## 튜토리얼 섹션

튜토리얼은 아래와 같이 구성되어 있다고한다.

- Setup for the Tutorial will give you a **starting point** to follow the tutorial.
- Overview will teach you **the fundamentals** of React: components, props, and state.
- Completing the Game will teach you the **most common techniques** in React development.
- Adding Time Travel will give you a **deeper insight** into the unique strengths of React.

한글로 표현하자면,

- [튜토리얼 환경설정](##-튜토리얼-환경설정)은 **어떻게 리액트를 시작할 지** 알려줄 것이다.
- [개요](##-개요)에서는 **리액트의 기본**인 **Components, props, state**에 대해 알려줄 것이다.
- [게임 완성하기](##-게임-완성하기)에서는 **리액트 개발에서 자주 쓰이는 기술**들에 대해 배울 수 있다.
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
나중에 코드를 수정하고 저장하면 별도로 명령을 재실행하지 않아도 반영된다.

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

[Before]

![Before](https://ko.reactjs.org/static/tictac-empty-1566a4f8490d6b4b1ed36cd2c11fe4b6-a9336.png)

[After]

![After](https://ko.reactjs.org/static/tictac-numbers-685df774da6da48f451356f33f4be8b2-be875.png)

`Before`에서 `After`로 화면이 바뀌었으면 성공이다. `Square`가 상위 컴포넌트인(혹은 parent) `Board`에서 데이터를 받아 화면으로 보여주는 방식이다.
만약, 결과가 다르다면 [링크](https://codepen.io/gaearon/pen/aWWQOG?editors=0010)의 코드와 비교하여 뭘 빠트렸는 지 확인하면 되겠다.

### 컴포넌트에 이벤트 추가하기

이제 `Square`를 클릭했을 때 `X`를 보여주도록 만들어보자. `Square`의 `render` 메소드를 다음과 같이 수정하자:

```javascript
class Square extends React.Component {
 render() {
   return (
     <button className="square" onClick={() => alert('click')}>
       {this.props.value}
     </button>
   );
 }
}
```

`Square`를 누르면 click 메세지와 함께 경고창이 뜬다. 여기서는 `=>` 처럼 ES6 문법인 arrow function이 사용되었다.
원래 목표는 사각형에 `X`를 띄우는 거란 걸 잊지말자. 이걸 위해서 `state`를 사용할 것이다.
리액트 컴포넌트는 생성자(constructor)에 `this.state` 를 써서 상태를 저장할 수 있다.
현재의 값을 `this.state`에 저장하고, `Square`가 클릭되었을 때 이 값을 바꿔주자.

우선, `Square` 컴포넌트에 생성자를 추가하고 초기화해주자:

```javascript
class Square extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: null,
    };
  }

  render() {
    return (
      <button className="square" onClick={() => alert('click')}>
        {this.props.value}
      </button>
    );
  }
}
```

> 여기서 잠깐!
모든 생성자를 가지는 리액트 컴포넌트 클래스는 반드시 `super(props)` 를 호출해야한다.

이제, `Square`의 `render` 메소드를 수정하자. 

- <button> 태그의 `this.props.value` 를 `this.state.value` 로 교체
- `onClick={...}` 내용을 `onClick={() => this.setState({value: 'X'})}` 로 교체
- 가독성을 위해 `className` `onClick` 라인 분리
  
완성본 :

```javascript
class Square extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: null,
    };
  }

  render() {
    return (
      <button
        className="square"
        onClick={() => this.setState({value: 'X'})}
      >
        {this.state.value}
      </button>
    );
  }
}
```

`Square`를 클릭하면 `render` 메소드의 `onClick`으로 인해 `Square`의 `this.state.value` 가 `X`가 될 것이다.
컴포넌트의 `setState`를 호출하면, 리액트는 자동적으로 하위 컴포넌트(혹은 자식, child)의 것도 바꾼다.
실행해서 클릭했을 때, 사각형에 `X`가 표시되는 지 확인하자.
안될 경우, [링크](https://codepen.io/gaearon/pen/VbbVLg?editors=0010) 확인!

### 개발 툴

[크롬](https://www.google.com/intl/ko_ALL/chrome/)이나 [파이어폭스](https://www.mozilla.org/ko/firefox/new/)에서 
리액트로 만든 페이지를 검사할 수 있다.

![검사 화면](https://ko.reactjs.org/static/devtools-878d91461c78d8f238e116477dfe0b46-6ca3b.png)

리액트 개발툴에서 `마우스 우클릭-검사`를 하면 브라우저 오른쪽에 탭이 열리면서 `props`나 `state`를 확인할 수 있다.

CodePen에서 진행하는 방법:

1. 로그인 / 회원가입 후 e-mail 인증(스팸 방지)
2. `Fork` 버튼 클릭
3. `Change View` 클릭 후 `Debug mode` 선택

## 게임 완성하기

이제는 `Square`를 클릭했을 때 `X` 와 `O`를 번갈아가면서 나오게하고, 승자를 판단하는 것을 추가해야한다.

### `state`를 부모(parent) 컴포넌트에게 전달하기

지금은 각각의 `Square`가 `state`를 가지고 있다. 누가 승자인지 판단하기 위해 9개의 `Square`의 `state`를 한 곳에서 체크해야한다.

`Board`가 각각의 `Square`의 `state`를 확인할 수도 있지만 이해하기가 좀 어렵고, 버그 걸리기 쉽고, refactor 하기 어려워 추천하지 않는다.
대신에, 우리는 각각의 `Square`가 아닌 `Board`에 게임의 `state`를 저장할 것이다. 그리고 이전에 우리가 각각의 사각형의 번호를 넘겼던 것처럼
`Board`가 `Square`에 `props`를 전달할 것이다.

**여러 자식들로부터 데이터를 가져오거나, 자식 컴포넌트 간 데이터를 주고 받아야할 때 공통된 `state`를 부모 컴포넌트에 선언해야한다.
부모 컴포넌트는 `props`를 통해 `state`를 자식 컴포넌트에게 전달할 수 있다. 이걸로 자식 컴포넌트들이 서로 동기화(sync) 될 수 있다.**

리액트 컴포넌트를 refactor 할 때, `state`를 부모 컴포넌트로 올리는 것을 자주 하게 될 것이니 이번 기회에 해보는 것이 좋다.

`Board`에 생성자를 추가하고, 생성자 `state`에 9개의 `Square`에 대응되도록 `squares`라는 사이즈 9짜리 배열을 선언하고 null 로 초기화하자:

```javascript
class Board extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      squares: Array(9).fill(null),
    };
  }

  renderSquare(i) {
    return <Square value={i} />;
  }
```

게임이 진행되면 `this.state.squares`는 이런 모습이 될 것이다:

```javascript
[
  'O', null, 'X',
  'X', 'X', 'O',
  'O', null, null,
]
```

지금 `Board`의 `renderSquare` 메소드는 이럴 것이다:
```javascript
  renderSquare(i) {
    return <Square value={i} />;
  }
```

이건 처음에 우리가 [value를 props를 통해 전달](###-props를-통해-데이터-전달하기)해서 **사각형에 0부터 8까지 숫자를 넣을 때** 작성한 코드이다.
하지만 우리가 [그 다음에 클릭한 경우 `X`의 `value`를 가진 `state`를 가지도록](###-컴포넌트에-이벤트-추가하기) 했고,
 `{this.state.value}` 를 읽도록 했기 때문에 숫자는 볼 수 없었다.

이제 `Board`의 `renderSquare` 메소드를 수정해서 우리가 만든 `squares` 배열을 이용하도록 할 것이다.

```javascript
 renderSquare(i) {
    return <Square value={this.state.squares[i]} />;
  }
```

[현재까지 코드 완성본](https://codepen.io/gaearon/pen/gWWQPY?editors=0010)

이제는 `Square`를 클릭했을 때의 이벤트를 바꿔줘야한다.(지금은 `X`값 세팅만 있다.) 그러기 위해서는 `Board`의 `state`를 업데이트 해줘야한다.
하지만 `state`는 해당 컴포넌트 내부에 선언되어 있어 `private`하기 때문에, `Square`가 `Board`의 `state`를 직접 변경할 수는 없다. 
대신에, 우리는 함수(function)를 호출하는 것으로 이를 해결할 것이다.

`Board`의 `renderSquare`를 아래와 같이 바꾸자:

```javascript
renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}
      />
    );
  }
```

이제 우리는 `Board`에서 `Square`로 2개의 `props`를 내려줄 것이다: `value`와 `onClick`.
`onClick` 이란 `prop`은 `Square`가 클릭 되었을 때 호출 될 것이다.
그리고 `Square`에 아래 3가지를 수정하자:

- `Square`의 `render` 메소드에서 `this.state.value`를 `this.props.value`로 변경
- `Square`의 `render` 메소드에서 `this.setState()`를 `this.props.onClick()`으로 변경
- `Square`의 생성자 삭제(이제 게임의 `state`를 여기서 관리하지 않는다)

다 반영하면, `Square` 컴포넌트는 이렇게 될 것이다:

```javascript
class Square extends React.Component {
  render() {
    return (
      <button
        className="square"
        onClick={() => this.props.onClick()}
      >
        {this.props.value}
      </button>
    );
  }
}
```

`Square`를 클릭했을 때, 어떻게 동작하게 되는 지 살펴보자:

1. `<button>` 안의 `onClick`이 리액트가 클릭 이벤트 리스너를 세팅하도록 명령한다.
2. 버튼이 클릭되었을 때, 리액트는 `Square`의 `render()`메소드 안에 있는 `onClick` 이벤트 핸들러를 호출한다.
3. 이벤트 핸들러는 `this.props.onClick()`을 호출한다. `Square`의 `onClick` prop은 `Board`에서 선언되어 있다.
4. 클릭되었을 때 `Board`가 `Square`로 `onClick={() => this.handleClick(i)}` 하도록 했기때문에, `Square`는 `this.handleClick(i)`를 호출한다.
5. 아직 `handleClick()` 메소드를 구현하지 않아서 사각형을 클릭하면 다음 에러가 발생할 것이다. 
``TypeError: _this3.handleClick is not a function''

`<button>`은 built-in 컴포넌트이기 때문에 `onClick` 을 써도 리액트가 이해할 수 있다.
하지만 `Square`처럼 커스텀 컴포넌트(이름을 새로 만든 경우)는 `Square`의 `onClick`prop이나 `Board`의 `handleClick` 메소드 중 아무거나 써도 된다.
리액트에서는 props의 경우에는 `on[Event]`로, method의 경우에는 `handle[Event]`를 쓰는 것이 일반적이다.

자 그럼 `Board`클래스 안에 `handleClick` 이벤트를 구현해보자:

```javascript
class Board extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      squares: Array(9).fill(null),
    };
  }

  handleClick(i) {
    const squares = this.state.squares.slice();
    squares[i] = 'X';
    this.setState({squares: squares});
  }

  renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}
      />
    );
  }

  render() {
    const status = 'Next player: X';

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
```

[완성본 링크](https://codepen.io/gaearon/pen/ybbQJX?editors=0010)

수정을 하고 실행해보면, 이전처럼 클릭했을 때 사각형에 `X`가 표시된다. 그럼 여태까지 뭐한거지라고 생각할 수도 있겠다.
다시 정리해보자면, 이전에는 각각의 `Square`에서 `state`를 관리했지만 이제는 `Board`에서 관리되기 때문에 여기서 승자를 결정할 수 있게 되었다.
`Board`의 `state`를 `Square`가 내려 받아 사용하므로 `Square`는 이제 **controlled components**라고 할 수 있다.
`Board`의 `state`가 바뀌면 `Square`는 자동적으로 `state`를 업데이트하여 다시 화면에 보여주게 된다.

`handleClick`을 보면 `.slice()`라는 함수를 통해 기존 배열을 수정하는 대신 `squares`의 복사본을 만들게 되었다.
이 이유는 다음 섹션에 설명하도록 하겠다.

### 변경불가성이 중요한 이유


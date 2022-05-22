## React Concept

#### 1. keyword
- Angular vs React vs Vue 비교 
- View를 다루는 라이브러리
- 랜더링과 업데이트에만 관여되는 라이브러리, 그렇기 때문에 다른 http 클라이언트나 스타일에 대한 기능은 없다.
- Component Based Development : 독립적인 코드 블럭 (HTTP + CSS + JavaScript)
- Virtual DOM : DOM을 직접 다루지 않고, 이를 React에게 위임함 
- JSX : 템플릿이 아니라 순수 js로 transpile되는 문법(Babel, TypeScript)
- CSR & SSR

#### 2. Component??
- src, class, name, props 밖에서 넣어주는 데이터
- 문서(HTML), 스타일(CSS), 동작(JS) 를 합쳐서 내가 만든 일종의 태그 
```html
<!-- HTMLElement -->
<img src="이미지 주소" />
<button class="클래스 이름">버튼</button>

<!-- 내가 만든 컴포넌트 -->
<내가지은이름1 name="SSW" />
<내가지은이름 prop={false}>내용</내가지은이름>
```

- React는 여러 개의 컴포넌트를 합쳐서 만든다. 


#### 3. React = Virtual DOM 사용
- DOM을 직접 제어하는 경우 : 바뀐 부분만 정확이 바꿔서 사용해야하기 때문에 불편
- DOM을 직접 제어하지 않는 경우(React) : 가상의 돔트리를 사용해서, 이전 상태와 이후 상태를 비교하여 바뀐 부분을 찾아내서 자동으로 바꾼다. 


#### 4. React Client Side Rendering (CSR)
1. 빈 껍데기의 html 파일이 들어온다. 
2. 그 html 파일 안에 경로로 js 파일을 요청한다. 
3. js 파일 안에는 React 웹 애플리케이션 전체가 들어있다. 
4. 그 React 웹 애플리케이션을 전체 다운 받는다.
5. 화면에 React Component가 나온다. 

#### 5. React Server Side Rendering (SSR)
1. 최초에 html로 표현되어 있는 html을 다운 받는다. 
2. html이 다운로드 되면 그 안에 있는 js를 다시 요청하는 과정에서는 html 구성요소가 Render되고 있는 상태이기 때문에 유저가 js 실행 전에 화면에 출력은 됨
3. js 다운로드 후 React 실행
4. js 동작 가능

#### 6. CSR vs SSR 
- CSR 
  - JS가 전부 다운로드 되어 리액트 애플리케이션이 정상 실행되기 전까지는 화면에 보이지 않음
  - JS가 전부 다운로드 되어 리액트 애플리케이션이 정상 실행된 후, 화면이 보이면서 유저가 인터렉션 가능 

- SSR
  - JS가 전부 다운로드 되지 않아도, 일단 화면은 보이지만 유저가 사용할 수 없음 
  - JS가 전부 다운로드 되어 리액트 애플리케이션이 정상 실행된 후, 유저가 사용 가능


<br>

## React Library

#### 1. 핵심 모듈
```js
// 리액트 컴포넌트 => HTMLElement 연결하는 역할
import ReactDOM from 'react-dom';

// 2. 리액트 컴포넌트 만드는 역할 
import React from 'react';
```


"만들어진 리액트 컴포넌트"를 실제 HTMLElement에 연결할 때 ReactDOM 라이브러리를 이용합니다.  

- React CDN
```html
<script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
```


#### 2. 기존 프론트엔트 
- HTML로 문서구조를 잡고
- CSS로 스타일을 입히고
- JS로 DOM을 조작한다.


#### 3. 컴포넌트를 활용한 프론트엔드 
- 컴포넌트를 정의하고
- 실제 DOM에 컴포넌트를 그려준다. 


## React Component 만드는 법 

#### Hooks 나오기 이전
- 컴포넌트 내부에 상태가 있다면 -> class 컴포넌트를 만들어서 사용 
- 컴포넌트 내부에 상태가 없다면 -> 라이프사이클은 사용해야하면 class
- 컴포넌트 내부에 상태가 없다면 -> 라이프사이클에 관계 없다면 function

#### Hooks 나온 후
- class
- function 
- 둘 모두 구분 없이 사용함


#### Class 컴포넌트 만들기 
```js
import React from 'react';

// 정의
class ClassComponent extends React.Component {
  render(){
    return (<div>Hello</div>);
  }
}

// 사용
<ClassComponent />
```


#### React.createElement로 컴포넌트 만들기 


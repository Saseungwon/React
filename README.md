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
https://github.com/Saseungwon/React/blob/master/React.createElement.html
- React.createElement의 한계
  ```html

    ReactDOM.render(
        React.createElement(
          "div", 
          null, 
          React.createElement(
            "div", 
            null,
            React.createElement("h1", null, "주제"), 
            React.createElement(
              "ul", 
              null, 
              react.createElement("li", null, "React"),
              react.createElement("li", null, "Vue"),
            )
          )
        ),
        document.querySelector('#root')
      );
  ```

#### JSX
- 위의 React.createElement의 한계를 해결하기 위해 
    ```html
        ReactDOM.render(
          <div a="a">
            <div>
            <h1>주제</h1>
            <ul>
              <li>Vue</li>
              <li>React</li>
            </ul>
            </div>
          </div>,
          document.querySelector("#root")
        );
    ```

- 우리가 작성한 어떤 코드를 순수하게 실행할 수 있는 자바스크립트로 변환하는 과정이 필요하다. => babel에 의해 진행됨
- JSX를 쓰는 이유
  - React.createElement 와 비교해서 가독성이 뛰어나다.
  - babel과 같은 컴파일 과정에서 문법적 오류를 인지하기 쉬움

- JSX 문법
  - 최상위 요소가 하나여야 한다. 
  - 최상위 요소 리턴하는 경우, ()로 감싸야 한다. 
  - 자식들을 바로 랜더링하고 싶으면, <>자식들</>을 사용한다. => Fragment
      ```html
        ReactDOM.render(
          <>  // fragment
          <div a="a">
            <div>
            <h1>주제</h1>
            <ul>
              <li>Vue</li>
              <li>React</li>
            </ul>
            </div>
          </div>,
          <div a="a">
            <div>
            <h1>주제</h1>
            <ul>
              <li>Vue</li>
              <li>React</li>
            </ul>
            </div>
          </div>,
          </>   // fragment
          document.querySelector("#root")
        );
    ```
  - 자바스크립트 표현식을 사용하려면 {표현식}을 이용한다.
      ```html
      const title = "주제!!!";

        ReactDOM.render(
          <div a="a">
            <div>
            <h1>{title}</h1>    // {}로 표현
            <ul>
              <li>Vue</li>
              <li>React</li>
            </ul>
            </div>
          </div>,
          document.querySelector("#root")
        );
    ``` 
  - if문 사용 불가능 -> 삼항 연사자 혹은 && 사용
  - style을 이용해 인라인 스타일링이 가능
  - class 대신 className을 사용해 class를 적용할 수 있다.
  - 자식요소가 있으면 꼭 닫아야 하고, 없으면 열면서 닫아야 한다. 
      ```html
      <p>자식요소</p>
      <br /> 
      ```

#### Props 와 State

Props : 컴포넌트 외부에서 컴포넌트에게 주는 데이터
State : 컴포넌트 내부에서 변경할 수 있는 데이터
둘다 변경이 발생하면, 랜더가 다시 일어날 수 있다. 

#### Render 함수
Props와 State를 바탕으로 컴포넌트를 그린다. 
그리고 Props와 State가 변경되면 컴포넌트를 다시 그린다. 
컴포넌트를 그리는 방법을 기술하는 함수가 랜더 함수이다.


#### Event Handling
- HTML DOM 에 클릭하면 이벤트가 발생하고, 발생하고 그에 맞는 변경이 일어나도록 해야한다. 
- JSX에 이벤트를 설정할 수 있다. 
<br>

- camelCase로만 사용가능 : onClick, onMouseEnter
- 이벤트에 연결된 자바스크립트 코드는 함수이다. : 이벤트 = {함수} 와 같이 쓴다. 
- 실제 DOM 요소들에만 사용 가능 : 리액트 컴포넌트에 사용하면 그냥 props로 전달한다.  


#### Component Lifecycle
- 리액트 컴포넌트는 탄생부터 죽음까지 여러 지점에서 개발자가 작업이 가능하도록 메서드를 오버라이딩 할 수 있게 해준다. 
<br>

- 리액트 라이프사이클의 성질
  - Declarative : 탄생부터 죽음까지 순간순간을 선언적으로 표현해놓으면 리액트 컴포넌트가 해당 상황이 되면 함수들을 실행할 수 있게 
    1. Component 생성 및 마운트
      - constructor
      - componentWillMount
      - render
      - componentDidMount

    2. Component props, state 변경
      - componentWillReceiveProps
      - shouldComponentUpdate
      - componentWillUpdate
      - render
      - componentDidUpdate

    3. Component 언마운트
      - componentWillUnmount
      - 언마운트 된 후에는 할 수 있는 게 없기 때문에 언마운트 되기 직전이라는 훅이 있다.(ex.정리할 메모리를 정리하는 처리)

- componentWillReceiceProps
  - props를 새로 지정했을 때 바로 호출된다.
  - 여기는 state의 변경에 반응하지 않는다. 
    - 여기서 props의 값에 따라 state를 변경해야 한다면
      - setState를 이용해 state를 변경한다. 그러면 다음 이벤트로 각각 가는것이 아니라 한 번에 변경된다. 

- shouldComponentUpdate
  - props만 변경되어도
  - state만 변경되어도
  - 둘다 변경되어도 
  - newProps와 new State를 인자로 해서 호출
  - return type은 boolean
    - true면 render
    - false면 render 호출 안 한다. 
    - default는 true

- componentWillUpdate
  - 컴포넌트가 재 랜더링 되기 직전에 불린다.
  - 여기선 setState 같은 것을 쓰면 안 된다. 

- componentDidUpdate 
  - 컴포넌트가 재 랜더링을 마치면 불린다.

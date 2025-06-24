## **React.js**

### **1. 기초 세팅 & 필수 툴 설치**

**모든 팀원이 똑같이 설치**

-   Node.js LTS 버전 설치 (최신 추천)    
-   VSCode 설치    
-   터미널/명령어 기본 연습    
-   GitHub 계정 만들기 + Git 기본 명령어
    
    
**bash**

    node -v
    npm -v
    git --version`

**공통 규칙 : VSCode 확장팩 설치**
-  ESLint (문법 검사기) : 코드에 문법 오류나 스타일 문제를 자동으로 찾아줌
- Prettier (코드 포맷터) : 자동으로 코드 정리해주는 도구 
- React Snippets (자동완성 단축키) : React 코드 빠르게 작성하는 확장팩



### **2. React 프로젝트 만들기**

**아래 명령어로 React 설치 및 프로젝트 생성까지 한번에 가능**

**bash**

    npx create-react-app my-app
    cd my-app
    npm start

### **3. 폴더 구조 이해**

React 프로젝트 생성 시 기본 폴더 구조

    my-app/
    ├─ node_modules/      → 설치된 라이브러리
    ├─ public/            → 정적 파일 (index.html 등)
    ├─ src/               → 핵심 소스 코드 작성 공간, 대부분의 개발 진행
    │   ├─ App.js         → 메인 컴포넌트 (화면의 틀)
    │   ├─ index.js       → 진입점 (React 앱 연결)
    │   └─ ...기타 파일
    ├─ package.json       → 프로젝트 설정 및 의존성 정보

### **4. JSX 문법 이해**

React는 HTML처럼 보이지만 실제로는 JS로 작성 
*JSX : JavaScript 안에 HTML을 쓰는 문법, HTML처럼 구조를 짤 수 있게 해줌.

**기본 규칙**
-   반드시 하나의 부모 태그로 감싸야 함    
-   class 대신 `className` 사용   
 -   JS 표현식은 `{ }` 안에 작성

**예시**
  

      function App() {
          return (
            <div>
              <h1>Hello, React!</h1>
              <p>이것은 JSX입니다.</p>
            </div>
          );
        }

### **5. 컴포넌트 기본 개념**

React는 UI를 작은 단위로 나눈 '컴포넌트'로 구성  

**종류**

-   함수형 컴포넌트 (주로 사용)    
-   클래스형 컴포넌트 (구형, 필요 시 학습)
    

**함수형 컴포넌트 예시**

    function Header() {
      return (
        <header>
          <h1>사이트 헤더</h1>
        </header>
      );
    }
    
    export default Header;

**App.js에서 사용**

    import Header from './Header';
    
    function App() {
      return (
        <div>
          <Header />
        </div>
      );
    }


### **6. Props (데이터 전달)**

부모 컴포넌트 → 자식 컴포넌트로 데이터 전달

**예시**

    function Welcome(props) {
      return <h1>안녕하세요, {props.name}님!</h1>;
    }
    
    function App() {
      return <Welcome name="홍길동" />;
    }

### **7. State (상태 관리)**

컴포넌트 내부에서 변하는 값 관리  
`useState` 사용

**예시**

    import { useState } from 'react';
    
    function Counter() {
      const [count, setCount] = useState(0);
    
      return (
        <div>
          <p>카운트: {count}</p>
          <button onClick={() => setCount(count + 1)}>증가</button>
        </div>
      );
    }

### **8. 이벤트 처리**

버튼 클릭 등 사용자 동작에 반응

`<button onClick={() =>  alert('버튼 클릭!')}>클릭</button>`


### **9. 반복 출력 (map 사용)**

배열 데이터를 반복 출력  

**예시**

    const items = ['사과', '바나나', '포도'];
    
    function ItemList() {
      return (
        <ul>
          {items.map((item, index) => (
            <li key={index}>{item}</li>
          ))}
        </ul>
      );
    }

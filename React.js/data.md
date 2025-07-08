# React.js 데이터 처리 정리

## 1. 제어 컴포넌트 (Controlled Component)

**정의:**

-   React의 상태(state)로 값을 제어하는 입력 요소
    
-   `value`와 `onChange`를 모두 지정해 사용자 입력과 상태를 동기화함
    

**예시:**

https://codesandbox.io/p/sandbox/dazzling-dijkstra-fzr452?file=%2Fsrc%2FApp.js%3A20%2C1

```jsx
import { useState } from "react";

export default function Example() {
  const [inputValue, setInputValue] = useState("");

  return (
    <div>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
        placeholder="입력해보세요"
      />
      <p>
        현재 입력값: <strong>{inputValue}</strong>
      </p>
    </div>
  );
}

```

**특징:**

-   값은 `state`에 저장됨
    
-   입력값 검증, 초기화, 동기화가 쉬움
    

----------

## 2. 입력 폼 처리

**기본 구조:**

-   입력값을 모두 `state`로 관리
    
-   제출 시 `state` 값 활용
    

**예시:**

https://codesandbox.io/p/sandbox/vqyxtf?file=%2Fsrc%2FApp.js%3A29%2C19

```jsx
import { useState } from "react";

export default function FormWithPreview() {
  const [formData, setFormData] = useState({
    name: "",
    email: "",
  });

  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData((prev) => ({
      ...prev,
      [name]: value,
    }));
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`제출 완료!\n이름: ${formData.name}\n이메일: ${formData.email}`);
  };

  return (
    <div style={{ padding: "20px", fontFamily: "sans-serif" }}>
      <h2>회원 가입</h2>
      <form onSubmit={handleSubmit}>
        <div>
          <label>
            이름:{" "}
            <input
              name="name"
              value={formData.name}
              onChange={handleChange}
              placeholder="이름 입력"
            />
          </label>
        </div>
        <div style={{ marginTop: "10px" }}>
          <label>
            이메일:{" "}
            <input
              name="email"
              value={formData.email}
              onChange={handleChange}
              placeholder="이메일 입력"
            />
          </label>
        </div>
        <button type="submit" style={{ marginTop: "15px" }}>
          제출
        </button>
      </form>

      <hr style={{ margin: "20px 0" }} />

      <h3>🔎 입력 내용 미리보기</h3>
      <p>이름: {formData.name || "(미입력)"}</p>
      <p>이메일: {formData.email || "(미입력)"}</p>
    </div>
  );
}


```

제어 컴포넌트 = 단일 입력 처리
입력 폼 처리 = 제어 컴포넌트를 여러 개 묶어서 다루기

----------

## 3. Create (데이터 추가)

**설명:**

-   새 항목을 배열에 추가하는 기본 패턴
    

**예시:**

```jsx
import { useState } from "react";

export default function CreateExample() {
  const [items, setItems] = useState([]);
  const [newItem, setNewItem] = useState("");

  const handleAdd = () => {
    if (newItem.trim() === "") return;
    setItems((prev) => [...prev, newItem]);
    setNewItem("");
  };

  return (
    <>
      <input value={newItem} onChange={(e) => setNewItem(e.target.value)} placeholder="새 항목" />
      <button onClick={handleAdd}>추가</button>
      <ul>
        {items.map((item, idx) => <li key={idx}>{item}</li>)}
      </ul>
    </>
  );
}

```

----------

## 4. Update (데이터 수정)

**설명:**

-   배열의 특정 항목을 수정하는 패턴
    

**예시:**

```jsx
import { useState } from "react";

export default function UpdateExample() {
  const [items, setItems] = useState(["React", "Vue"]);
  const [editIndex, setEditIndex] = useState(null);
  const [editValue, setEditValue] = useState("");

  const startEdit = (idx) => {
    setEditIndex(idx);
    setEditValue(items[idx]);
  };

  const saveEdit = () => {
    setItems((prev) =>
      prev.map((item, idx) => (idx === editIndex ? editValue : item))
    );
    setEditIndex(null);
  };

  return (
    <ul>
      {items.map((item, idx) => (
        <li key={idx}>
          {editIndex === idx ? (
            <>
              <input value={editValue} onChange={(e) => setEditValue(e.target.value)} />
              <button onClick={saveEdit}>저장</button>
            </>
          ) : (
            <>
              {item} <button onClick={() => startEdit(idx)}>수정</button>
            </>
          )}
        </li>
      ))}
    </ul>
  );
}

```

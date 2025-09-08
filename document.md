## Mini To-Do List 기술 명세서 (입문자용)

### 문서 목적
이 문서는 입문자가 이번 빌드(단일 HTML 파일로 만든 Mini To-Do List)의 구조와 동작 원리를 빠르게 이해할 수 있도록 돕습니다. 코드와 개념을 간단하고 실용적으로 설명합니다.

### 빌드 산출물
- **주요 파일**: `index.html` (HTML/CSS/JavaScript가 모두 한 파일에 포함)
- **실행 방법**: 파일을 더블 클릭하여 브라우저(Chrome/Edge 등)로 열면 바로 동작

### 목표(Requirements)
- **단일 파일 구성**: HTML, CSS, JS를 하나의 파일에 포함
- **할 일 추가**: 텍스트 입력 후 “추가” 버튼 또는 Enter로 목록에 아이템 추가
- **완료 토글**: 목록 항목을 클릭(또는 Enter/Space)하면 완료/미완료 전환 및 줄 긋기 표시
- **입문자 친화 주석**: 배열과 DOM 리스트 관리 개념을 충분한 주석으로 설명

### 주요 기능 요약
- **입력 및 추가**: 입력창(`input#todo-input`)과 버튼(`button#add-btn`)으로 새 할 일을 배열에 추가
- **렌더링(Render)**: 배열 상태를 기준으로 `<ul#todo-list>`에 `<li>` 항목을 다시 그림
- **완료 표시**: 항목 클릭(또는 키보드 조작) 시 `completed` 상태를 토글, 줄 긋기 스타일 적용
- **접근성(Accessibility)**: 키보드 포커스/Enter/Space 지원, 시각적 포커스 링 제공

### 기술 스택 및 구조
- **HTML**: 화면의 기본 구조(입력, 버튼, 목록 영역)
- **CSS**: 어두운 테마, 버튼/입력 포커스, 완료 상태 스타일(줄 긋기)
- **JavaScript**: 배열로 데이터 관리, 이벤트 바인딩, 렌더링 함수 구현

### 데이터 모델
- **배열 구조**: `todos: Array<TodoItem>`
- **아이템 타입**: `TodoItem = { id: number, text: string, completed: boolean }`
- **id 생성**: `nextId`를 증가시키는 간단한 방식 사용(실무에서는 uuid 등 대체 가능)

### 상태 관리와 렌더링 흐름
1) 사용자가 텍스트 입력 후 “추가” 버튼(또는 Enter)을 누름
2) `addTodoFromInput()`가 입력값을 검사하고 `todos.push(newItem)` 수행
3) `renderList()`가 호출되어 `<ul>` 내용을 전부 지우고, `todos`를 기반으로 `<li>`를 다시 생성
4) 각 `<li>`는 `data-id`를 통해 자신의 아이템 id를 보유하며, `completed`면 `completed` 클래스를 가짐
5) 항목 클릭(또는 Enter/Space) 시 해당 id를 찾아 `completed`를 토글하고 다시 `renderList()` 호출

### 이벤트 처리(핵심 포인트)
- **추가 이벤트**
  - 버튼 클릭: `addBtnEl.addEventListener('click', addTodoFromInput)`
  - 입력창 Enter: `inputEl.addEventListener('keydown', ...)`
- **토글 이벤트(이벤트 위임)**
  - `ul#todo-list`에 한 번만 리스너를 등록하고, 실제 클릭된 요소의 상위에서 `li.todo-item`를 찾아 처리
  - 키보드 조작(Enter/Space)도 동일한 원리로 처리하여 접근성 향상

### 스타일 가이드(요약)
- 어두운 배경과 대비되는 텍스트 색상
- 포커스 시 테두리/그림자 강조(접근성)
- 완료 항목은 `text-decoration: line-through`와 흐린 색상 적용

### 접근성 고려 사항
- `aria-label`을 사용해 버튼/목록 의미 부여
- `tabindex`로 리스트 항목 포커스 가능
- 키보드 조작(Enter/Space) 지원으로 마우스 없이도 조작 가능

### 사용 방법
1) `index.html`을 브라우저로 엽니다.
2) 입력창에 할 일을 적고 Enter 또는 “추가” 버튼을 누릅니다.
3) 목록에 나타난 항목을 클릭(또는 포커스 후 Enter/Space)하면 완료 상태가 전환됩니다.

### 확장 아이디어(선택)
- 로컬 스토리지 저장/불러오기(`localStorage`)로 새로고침 후에도 목록 유지
- 항목 삭제 버튼 추가, 전체 삭제 기능
- 필터(전체/미완료/완료) 탭 추가
- 드래그 앤 드롭으로 순서 변경

### 코드 스니펫(참고)
아래는 배열을 화면에 그려주는 핵심 함수의 축약 예시입니다. 실제 구현은 `index.html`에 있습니다.

```javascript
function renderList() {
  listEl.innerHTML = '';
  for (const item of todos) {
    const li = document.createElement('li');
    li.className = 'todo-item' + (item.completed ? ' completed' : '');
    li.dataset.id = String(item.id);
    li.textContent = item.text; // 실제 구현은 dot/span 등 요소를 더 구성
    listEl.appendChild(li);
  }
}
```

### 테스트 체크리스트
- 입력 후 “추가” 클릭 시 목록에 항목이 생기는가?
- 입력 후 Enter 키로도 동일하게 추가되는가?
- 항목 클릭 시 줄 긋기가 토글되는가?
- 키보드(탭 이동 → Enter/Space)로도 동일하게 동작하는가?

### 결론
본 빌드는 배열과 DOM 렌더링의 기본 개념을 학습하기 좋도록 최소한의 구조로 제작되었습니다. 하나의 파일로 실행과 독해가 쉬우며, 확장도 간단히 시도해볼 수 있습니다.



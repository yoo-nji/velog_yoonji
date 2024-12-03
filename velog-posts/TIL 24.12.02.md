<h2 id="📚-til">📚 TIL</h2>
<p>useReducer (별도 포스팅 예정)</p>
<ul>
<li>코테 공부 - 스택</li>
<li><del>useReducer 예제 복습</del></li>
<li><del>당일 과제 TODO 만들기(등록, 추가, 삭제)</del></li>
</ul>
<h2 id="💬-마치며">💬 마치며</h2>
<p><strong>TODO 과제 회고</strong></p>
<p>id 값을 설정할 때 초기에는 배열의 마지막 인덱스를 기준으로 id를 설정했는데, 배열 변경이 일어날 경우 예상치 못한 충돌이나 변경 문제가 발생할 가능성이 있었다. 그래서 useRef를 활용해 id 값을 관리하는 방식으로 변경</p>
<p>기존 코드</p>
<pre><code class="language-tsx">// 마지막 배열 인덱스 번호로 id 설정
 const lastIndex = todos[todos.length - 1].id + 1;</code></pre>
<p>변경 코드</p>
<pre><code class="language-tsx"> //id
  const idRef = useRef(0);

  // 투두리스트 추가 함수
  const addTodo = (value: string) =&gt; {
    if (value.trim() === &quot;&quot;) {
      alert(&quot;내용을 입력해 주세요&quot;);
      inputRef.current?.focus();
    } else
      setTodos((todos) =&gt; [
        ...todos,
        { id: idRef.current++, content: value, completed: false },
      ]);
    setInput(&quot;&quot;);
    inputRef.current?.focus();
  };
</code></pre>
<p>분명 더 좋은 코드가 있겠지만... 이번 과제를 통해 useRef가 DOM 조작 외에도 다양한 상황에서 활용될 수 있다는 것을 알게 됐다 </p>
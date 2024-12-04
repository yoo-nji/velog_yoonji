<h2 id="📚-til">📚 TIL</h2>
<ol>
<li>useEffect</li>
</ol>
<ul>
<li>함수형 컴포넌트의 생명주기를 관리하는 React Hook</li>
<li>컴포넌트의 마운트, 업데이트, 언마운트 시점에 특정 작업 수행</li>
<li>실습: Todo 리스트에서 로컬스토리지를 활용한 데이터 영속성 구현</li>
</ul>
<ol start="2">
<li>메모이제이션</li>
</ol>
<ul>
<li><p>불필요한 리렌더링을 방지</p>
<ul>
<li>React.memo(): 컴포넌트 자체를 메모이제이션</li>
<li>useCallback(): 함수를 메모이제이션</li>
<li>useMemo(): 계산값을 메모이제이션</li>
</ul>
<p><strong>최적화 적용 순서</strong></p>
<ol>
<li>컴포넌트 메모이제이션 (React.memo)</li>
<li>참조형 props 메모이제이션 (useCallback, useMemo)</li>
</ol>
<ul>
<li>실습: Todo 리스트 컴포넌트 최적화 구현</li>
</ul>
</li>
</ul>
<ol start="3">
<li>전역상태관리</li>
</ol>
<ul>
<li>Context API를 통한 전역 상태 관리<ul>
<li>전역 상태를 여러 컴포넌트에서 공유할 수 있음</li>
<li>불필요한 props drilling 방지</li>
</ul>
</li>
</ul>
<ol start="4">
<li>useId</li>
</ol>
<ul>
<li>서버사이드 렌더링 환경에서도 안정적인 고유 ID 생성</li>
<li>접근성 향상을 위한 라벨-폼 요소 연결에 활용</li>
<li>실습: Todo 리스트의 체크박스-라벨 연결에 useId 활용</li>
</ul>
<h2 id="💬-마치며">💬 마치며</h2>
<p>useEffect, 메모이제이션 응용 연습이 필요할 것 같다. 뭔가 사용해 보려고 하면 감이 안 잡힘... 포스팅은 머리에서 정리가 되는대로 해봐야지 ^.^</p>
<h2 id="호이스팅">호이스팅</h2>
<p><strong>호이스팅</strong>: 자바스크립트 엔진이 코드 실행 전 변수와 함수의 선언부를 스코프의 최상단으로 끌어올리는 동작. <code>면접단골</code></p>
<p>자바스크립트는 <code>인터프리터</code> 기반 언어로, 코드를 순차적으로 실행하지만 호이스팅으로 인해 선언부가 먼저 처리됨.</p>
<h3 id="변수와-함수-호이스팅-시-처리-방식"><strong>변수와 함수 호이스팅 시 처리 방식</strong></h3>
<ol>
<li><p><strong>변수 호이스팅</strong></p>
<pre><code class="language-jsx"> console.log(&quot;name&quot;); //undefined
 console.log(&quot;age&quot;); //undefined
 var name = &quot;윤지&quot;;
 var age = 24;</code></pre>
<ul>
<li><strong>var:</strong> <strong>undefined</strong>로 초기화됨</li>
<li><strong>let과 const:</strong> 초기화되지 않은 상태로 메모리에 등록, <strong>일시적 사각지대(TDZ)</strong>에 진입<ul>
<li>코드 실행 중 명확한 값 할당 시에만 에러 없이 접근 가능함</li>
</ul>
</li>
</ul>
</li>
<li><p><strong>함수 선언식 호이스팅</strong></p>
<pre><code class="language-jsx"> print(); // 호출 가능 (호이스팅 적용)

 function print() {
   console.log(&quot;a&quot;);
 }</code></pre>
<ul>
<li>함수 전체가 메모리에 등록됨</li>
<li>코드의 어디에서든 호출 가능함</li>
</ul>
</li>
<li><p><strong>함수 표현식의 호이스팅</strong></p>
<pre><code class="language-jsx"> print(); // 오류 발생 (Cannot access 'print' before initialization)

 const print = function () {
   console.log(&quot;a&quot;);
 };</code></pre>
<ul>
<li>변수 선언부만 호이스팅되고, 변수에 undefined 할당 (var로 선언 시)</li>
<li>let이나 const로 선언된 함수 표현식은 <strong>초기화되지 않은 상태</strong>로 TDZ에 머무름</li>
<li><strong>선언 이전 호출 시 에러</strong> 발생함</li>
</ul>
</li>
</ol>
<h2 id="실행-컨텍스트와-스코프">실행 컨텍스트와 스코프</h2>
<p>호이스팅의 발생 이유 이해를 위해 <code>실행컨텍스트</code>에 대한 이해 필요</p>
<h3 id="실행-컨텍스트">실행 컨텍스트</h3>
<p>실행컨텍스트: 자바스크립트를 실행하는 독립적인 공간</p>
<p><strong>실행 컨텍스트의 역할과 중요성</strong></p>
<p>실행 컨텍스트: 자바스크립트 코드 실행 환경. '레코드' 공간에 변수와 함수 이름을 미리 기록하여 다음 기능 수행:</p>
<ul>
<li>변수와 함수의 쉬운 접근성 보장</li>
<li>코드의 예측 가능한 동작 지원</li>
<li>변수 검색 우선순위 설정</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/23cc224c-b83b-4a60-8e0c-32429f034c82/image.png" /></p>
<p><strong>구성 요소</strong></p>
<p>실행 컨텍스트의 두 가지 주요 구성 요소:</p>
<ul>
<li><strong><code>Record</code></strong>: 변수와 함수 선언을 저장하는 컴포넌트</li>
<li><strong><code>Outer</code></strong>: 상위 스코프를 연결하는 통로<ul>
<li>내부 스코프에서 변수 찾을 때, 상위 스코프(외부 환경)를 순서대로 탐색</li>
<li>이 과정을 <strong><code>스코프 체이닝</code></strong>이라고 함</li>
<li>최종적으로 전역 스코프까지 찾아가고, 거기에도 없으면 &quot;name is not defined&quot; 에러 발생</li>
</ul>
</li>
</ul>
<p><strong>실행 컨텍스트 순서</strong></p>
<ol>
<li><strong>생성</strong>: 변수, 함수 선언 부분 기록<ol>
<li>변수를 선언하고 <strong>초기화</strong><ul>
<li>var 변수: undefined 할당</li>
<li>let/const 변수: 초기화되지 않은 상태로 TDZ에 존재<ul>
<li>일시적 사각지대(TDZ): 선언부터 초기화 전까지의 구간</li>
</ul>
</li>
</ul>
</li>
<li>this 키워드를 바인딩</li>
<li>스코프 범위 결정</li>
</ol>
</li>
<li><strong>실행</strong>: 선언 부분 참조하여 실행<ul>
<li>전역 컨텍스트에서 실행 중 함수 만나면 함수 실행 컨텍스트 생성하여 스택에 추가</li>
</ul>
</li>
</ol>
<p><strong>주요 유형</strong></p>
<ul>
<li>전역 실행 컨텍스트: 자바스크립트 프로그램이 처음 시작될 때 만들어지는 기본 컨텍스트</li>
<li>함수 실행 컨텍스트: 함수가 호출될 때마다 생성되는 컨텍스트</li>
</ul>
<h3 id="콜-스택">콜 스택</h3>
<p>콜 스택: 실행 컨텍스트를 관리하는 자료구조</p>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/252f95a4-cc8e-4eba-bc2e-02aff23d6134/image.png" /></p>
<p>콜스택</p>
<ul>
<li>프로그램 실행 시 '전역 실행 컨텍스트' 생성 및 스택에 '푸시'</li>
<li>스택은 <strong>후입선출</strong> 방식으로 작동, 마지막에 쌓인 것을 먼저 처리</li>
<li>함수 호출 시마다 해당 함수의 실행 컨텍스트를 스택에 푸시</li>
<li>함수 실행 완료 시 해당 컨텍스트를 스택에서 '팝'</li>
<li>모든 실행 컨텍스트 처리 및 스택이 비워지면 프로그램 실행 종료</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/b544b305-0e39-418a-9a12-e1ec3628f7fe/image.png" /></p>
<p>함수 실행 컨텍스트가 스택에 푸시된 상태</p>
<p><strong>푸시(Push)와 팝(Pop)</strong></p>
<ul>
<li><strong>푸시:</strong> 스택 최상단에 항목 추가. 콜 스택에서 새 실행 컨텍스트 추가 시 사용.</li>
<li><strong>팝:</strong> 스택 최상단 항목 제거. 콜 스택에서 함수 실행 완료 시 컨텍스트 제거에 사용.</li>
</ul>
<h3 id="스코프">스코프</h3>
<p>스코프: 실행컨텍스트 안에서 실행되는 유효한 범위</p>
<p>하나의 실행컨텍스트가 하나의 스코프를 갖게 됨(실행컨텍스트 ≠ 스코프)</p>
<ul>
<li>전역 스코프: 어디서든 접근 가능한 변수나 함수</li>
<li>지역 스코프: 특정 함수 내에서만 접근 가능한 변수나 함수</li>
</ul>
<p>출처 <a href="https://www.sucoding.kr">수코딩</a></p>
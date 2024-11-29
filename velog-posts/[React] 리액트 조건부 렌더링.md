<h3 id="react에서의-조건부-렌더링">React에서의 조건부 렌더링</h3>
<p>React에서 조건부 렌더링은 특정 조건에 따라 컴포넌트를 표시하거나 숨길 때 사용</p>
<hr />
<h2 id="1-if문-사용">1. <strong>if문 사용</strong></h2>
<p><code>JSX 외부</code>에서 조건에 따라 전체 컴포넌트 또는 JSX 블록을 처리할 때 유용함</p>
<h3 id="예제-컴포넌트-렌더링"><strong>예제: 컴포넌트 렌더링</strong></h3>
<pre><code class="language-tsx">import Login from &quot;../Login&quot;;
import Logout from &quot;../Logout&quot;;

export default function IfExample() {
  const isLoggedIn = true;

  if (isLoggedIn) {
    return &lt;Login /&gt;;
  }
  return &lt;Logout /&gt;;
}</code></pre>
<h3 id="예제-간단한-메시지-출력">예제: 간단한 메시지 출력</h3>
<pre><code class="language-tsx">export default function IfExample() {
  const isLoggedIn = false;

  if (isLoggedIn) {
    return &lt;h2&gt;환영합니다!&lt;/h2&gt;;
  }
  return &lt;h2&gt;로그인이 필요합니다.&lt;/h2&gt;;
}</code></pre>
<hr />
<h2 id="2-삼항-연산자">2. <strong>삼항 연산자</strong></h2>
<p><code>JSX 내부</code>에서 <code>참과 거짓</code>에 따라 다른 요소를 렌더링할 때 사용</p>
<h3 id="1-단순-텍스트-조건부-렌더링">1. 단순 텍스트 조건부 렌더링</h3>
<pre><code class="language-tsx">export default function TernaryExample() {
  const isLoggedIn = true;

  return (
    &lt;&gt;
      &lt;h1&gt;{isLoggedIn ? &quot;로그인 되었습니다&quot; : &quot;로그인이 필요합니다&quot;}&lt;/h1&gt;
    &lt;/&gt;
  );
}</code></pre>
<h3 id="2-jsx-요소-조건부-렌더링">2. JSX 요소 조건부 렌더링</h3>
<pre><code class="language-tsx">{isLoggedIn ? &lt;h1&gt;로그인 되었습니다&lt;/h1&gt; : &lt;h1&gt;로그인 되지 않았습니다&lt;/h1&gt;}</code></pre>
<h3 id="3-컴포넌트-조건부-렌더링">3. 컴포넌트 조건부 렌더링</h3>
<pre><code class="language-tsx">{isLoggedIn ? &lt;Login /&gt; : &lt;Logout /&gt;}</code></pre>
<h3 id="4-인라인-스타일-조건부-적용">4. 인라인 스타일 조건부 적용</h3>
<pre><code class="language-tsx">&lt;h1 style={{ color: isLoggedIn ? &quot;red&quot; : &quot;blue&quot; }}&gt;로그인&lt;/h1&gt;</code></pre>
<h3 id="5-클래스명-조건부-적용">5. 클래스명 조건부 적용</h3>
<pre><code class="language-tsx">&lt;h1 className={`${isLoggedIn ? &quot;text-rose-400&quot; : &quot;text-green-600&quot;}`}&gt;로그인&lt;/h1&gt;</code></pre>
<h3 id="6-tailwind-merge를-활용한-조건부-스타일링">6. Tailwind Merge를 활용한 조건부 스타일링</h3>
<pre><code class="language-tsx">&lt;h1 className={twMerge(isLoggedIn ? &quot;text-rose-400&quot; : &quot;text-gray-500&quot;)}&gt;로그인&lt;/h1&gt;</code></pre>
<hr />
<h2 id="3--연산자">3. <strong>&amp;&amp; 연산자</strong></h2>
<p>JSX 범위 안에서 <code>참</code>에 따른 분기 처리를 하고 싶을 때</p>
<h3 id="예제-특정-컴포넌트-렌더링">예제: 특정 컴포넌트 렌더링</h3>
<pre><code class="language-tsx">import Login from &quot;../Login&quot;;
// 내가 true일 때만 렌더링하고 싶을 때 사용
// flase는 신경 안 쓰고 싶다! 하면 이렇게
export default function AndExample() {
  const isLoggedIn = true;

  return (
    &lt;&gt;
      {isLoggedIn &amp;&amp; &lt;Login /&gt;}
      &lt;h2&gt;이 메시지는 항상 보입니다.&lt;/h2&gt;
    &lt;/&gt;
  );
}</code></pre>
<h3 id="예제-클래스-이름-적용">예제: 클래스 이름 적용</h3>
<pre><code class="language-tsx">import { twMerge } from &quot;tailwind-merge&quot;;

export default function AndExample() {
  const isLoggedIn = true;

  return (
     {/* 클래스네임 조건부 */}
      {/* style로는 불가능 */}
    &lt;h1 className={twMerge(isLoggedIn &amp;&amp; &quot;text-green-600&quot;)}&gt;
      조건부 클래스 적용
    &lt;/h1&gt;
  );
}
</code></pre>
<hr />
<h2 id="4-즉시-실행-함수-iife">4. <strong>즉시 실행 함수 (IIFE)</strong></h2>
<p>🤔 <strong>JSX 표현식에서 if문 사용 불가?</strong> 놉, IIFE(즉시실행함수)로 사용 가능</p>
<p><strong>IIFE를 사용하여 JSX 표현식 내에서 if문을 사용하는 방법</strong></p>
<ol>
<li>함수를 소괄호 ()로 감싸기</li>
<li>함수를 즉시 실행하기 위해 끝에 ()를 추가</li>
<li>함수 내부에서 일반적인 if-else 문 사용 가능</li>
</ol>
<h3 id="예제-if문으로-조건부-렌더링">예제: if문으로 조건부 렌더링</h3>
<pre><code class="language-tsx">export default function IIFE() {
  const isLoggedIn = true;

  return (
    &lt;&gt;
      {(() =&gt; {
        if (isLoggedIn) {
          return &lt;h2&gt;로그인 되었습니다&lt;/h2&gt;;
        } else {
          return &lt;h2&gt;로그인이 필요합니다&lt;/h2&gt;;
        }
      })()}
    &lt;/&gt;
  );
}
</code></pre>
<blockquote>
<p>💡 참고: IIFE 활용 시 JSX 표현식 내부에서도 if문 사용 가능. 단, 가독성을 위해 외부 처리나 삼항/&amp;&amp; 연산자 사용이 일반적임</p>
</blockquote>
<hr />
<h2 id="조건부-렌더링의-선택-기준"><strong>조건부 렌더링의 선택 기준</strong></h2>
<table>
<thead>
<tr>
<th><strong>방법</strong></th>
<th><strong>사용 상황</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>if문</strong></td>
<td>JSX <strong>외부</strong>에서 전체 블록 또는 컴포넌트를 조건부로 처리할 때</td>
</tr>
<tr>
<td><strong>삼항 연산자</strong></td>
<td>JSX <strong>내부</strong>에서 <code>참</code>과 <code>거짓</code>에 따라 다른 결과를 렌더링할 때</td>
</tr>
<tr>
<td><strong>&amp;&amp; 연산자</strong></td>
<td>JSX <strong>내부</strong>에서 ****조건이 <code>참</code>일 때만 특정 요소를 렌더링할 때</td>
</tr>
</tbody></table>
<h2 id="1-타입-단언-type-assertion">1. <strong>타입 단언 (Type Assertion)</strong></h2>
<ul>
<li><p>개발자가 타입스크립트에게 🗣️ &quot;<strong>이 값의 타입은 내가 더 잘 앎</strong>&quot;이라고 알리는 기능</p>
<p>  ⇒ 타입스크립트 컴파일러는 이를 무조건 신뢰하고 따름</p>
</li>
<li><p><strong>사용목적:</strong> 타입스크립트가 타입을 추론하지 못하거나, 명확히 타입을 지정해야 하는 상황에서 사용</p>
</li>
<li><p><strong>TypeScript 문법</strong></p>
<ol>
<li><code>&lt;&gt;</code> 문법 (거의 미사용) <strong>JSX 환경</strong>에서 React의 태그 문법과 충돌 가능</li>
<li><code>as</code> 문법 (주로 사용)</li>
</ol>
</li>
</ul>
<pre><code class="language-tsx">let value: string = &quot;hi&quot;;

// 방법 1: &lt;&gt;
(&lt;string&gt;value).toUpperCase();

// 방법 2: as
(value as string).toUpperCase();</code></pre>
<p>⚠️ <strong>주의</strong></p>
<ul>
<li>남용하면 컴파일러가 잘못된 타입 단언을 무시해 TypeScript의 장점(타입 안전성)이 사라질 수 있음</li>
<li>타입 단언으로 발생하는 모든 에러는 개발자의 책임</li>
</ul>
<h3 id="타입-단언-사용예">타입 단언 사용예</h3>
<ul>
<li><p><strong>DOM 요소 접근</strong></p>
<ul>
<li><p>타입스크립트는 DOM 요소의 타입을 명확히 추론하지 못하는 경우가 있음. 이런 경우, 타입을 정확히 명시해서 에러 해결</p>
<pre><code class="language-tsx">const button = document.getElementById(&quot;button&quot;);

// 에러 발생: 'null'일 가능성 있음
// button.click();

// 해결 방법 1: 타입 단언 사용 (as)
(button as HTMLElement).click();

// 해결 방법 2: 타입 단언 사용 (&lt;&gt;)
(&lt;HTMLElement&gt;button).click(); // ✅ 타입을 명시하여 에러 해결</code></pre>
<blockquote>
<p><strong><code>HTMLElement</code></strong></p>
<p> : 버튼과 같은 HTML 요소를 표현하는 타입스크립트의 기본 타입</p>
</blockquote>
</li>
</ul>
</li>
<li><p><strong>API 응답 데이터</strong></p>
<p>  서버로부터 받은 데이터의 타입 지정 시 사용. 타입스크립트는 서버에서 어떤 JSON이 반환될지 알지 못해 response.json()의 타입이 Promise로 타입추론됨. 타입 단언을 사용하면 명확한 타입을 지정하여 자동완성과 타입 체크 가능</p>
<pre><code class="language-tsx">  type User = { id: number; name: string };

  const response = await fetch(&quot;/api/user&quot;);
  const userData = (await response.json()) as User; // Promise&lt;any&gt;를 User 타입으로 단언
  console.log(userData.name);</code></pre>
</li>
</ul>
<h2 id="2-타입-가드-type-guard">2. <strong>타입 가드 (Type Guard)</strong></h2>
<ul>
<li><strong>정의</strong>: 조건문을 통해 <strong>값의 타입을 확인하고 좁히는 기능</strong></li>
<li><strong>주요 특징</strong>:<ul>
<li>TypeScript와 JavaScript 모두에서 사용 가능</li>
<li>조건문 안에서만 타입이 보장</li>
<li><strong><code>typeof</code>, <code>instanceof</code></strong> 등을 활용</li>
</ul>
</li>
<li><strong>예시</strong><ul>
<li><code>typeof</code>를 사용하여 <code>unknown</code> 타입을 <code>string</code>으로 좁히는 예제</li>
</ul>
</li>
</ul>
<pre><code class="language-tsx">let value: unknown = &quot;hi&quot;;
if (typeof value === &quot;string&quot;) {
  console.log(value.toUpperCase()); // HI
}</code></pre>
<h2 id="3-타입-단언과-타입-가드-비교">3. 타입 단언과 타입 가드 비교</h2>
<table>
<thead>
<tr>
<th><strong>특성</strong></th>
<th><strong>타입 단언</strong></th>
<th><strong>타입 가드</strong></th>
</tr>
</thead>
<tbody><tr>
<td>언어</td>
<td>TypeScript 전용</td>
<td>TypeScript와 JavaScript 모두 사용 가능</td>
</tr>
<tr>
<td>역할</td>
<td>개발자가 직접 타입 선언</td>
<td>조건문으로 런타임에 타입 확인 및 좁힘</td>
</tr>
<tr>
<td>타입 안전성</td>
<td>잘못된 단언 시 안전성 상실</td>
<td>조건을 통해 타입이 안전하게 좁힘</td>
</tr>
<tr>
<td>사용 시점</td>
<td>컴파일 시(정적)</td>
<td>런타임 시(동적)</td>
</tr>
<tr>
<td>주요 문법</td>
<td>as 키워드 또는 &lt;&gt; 기호</td>
<td>typeof, instanceof 등의 연산자</td>
</tr>
</tbody></table>
<h3 id="요약"><strong>요약</strong></h3>
<ul>
<li><strong>타입 단언</strong>: 컴파일러가 타입을 추론하지 못하는 상황에서 개발자가 직접 타입을 선언. 신중한 사용 필요</li>
<li><strong>타입 가드</strong>: 조건문으로 타입을 확인하고 안전하게 좁히는 기능. 타입 안정성을 보장해 선호</li>
</ul>
<h2 id="1-타입-단언-type-assertion">1. 타입 단언 (Type Assertion)</h2>
<p><strong><code>타입 단언이란?</code></strong> 개발자가 타입스크립트에게 🗣️ &quot;<strong>이 값의 타입은 내가 더 잘 앎</strong>&quot;이라고 알려주는 기능</p>
<p><strong>사용목적:</strong>  WEB API 사용 시 타입 추론을 제대로 못하는 경우 사용</p>
<h3 id="11-타입-단언-사용법">1.1 타입 단언 사용법</h3>
<ol>
<li><code>&lt;&gt;</code> 문법 (거의 사용하지 않음)</li>
<li><code>as</code> 문법 (더 많이 사용됨)</li>
</ol>
<pre><code class="language-tsx">let value: string = &quot;hi&quot;;

// 방법 1: &lt;&gt;
(&lt;string&gt;value).toUpperCase();

// 방법 2: as
(value as string).toUpperCase();</code></pre>
<blockquote>
<p>⚠️ <strong>주의</strong>: 타입 단언으로 발생하는 모든 에러는 개발자의 책임</p>
</blockquote>
<h3 id="12-타입-단언의-활용-예시-dom-요소-접근">1.2 타입 단언의 활용 예시: DOM 요소 접근</h3>
<p>타입스크립트는 DOM 요소의 타입을 명확히 추론하지 못하는 경우가 많음. 이런 경우, 타입 단언을 활용하면 에러 해결 가능</p>
<pre><code class="language-tsx">const button = document.getElementById(&quot;button&quot;);

// 에러 발생: 'null'일 가능성 있음
// button.click();

// 해결 방법 1: 타입 단언 사용
(button as HTMLElement).click(); // ✅ 타입을 명시하여 에러 해결

// 해결 방법 2: 옵셔널 체이닝(js) 연산자 사용
button?.click(); // ✅ 안전하게 버튼이 존재할 때만 실행

// 해결 방법 3: 널 아님 단언(ts) 연산자 사용
button!.click(); // ✅ 널이 아님을 보장</code></pre>
<h2 id="2-타입-가드-type-guard">2. 타입 가드 (Type Guard)</h2>
<p><strong><code>타입 가드</code></strong>는 <strong>자바스크립트</strong>의 조건문을 활용하여 변수의 타입을 좁혀주기 위해 사용</p>
<p><strong>런타임에 타입을 확인</strong>하고 안전하게 타입에 맞는 동작을 수행할 수 있도록 도움</p>
<h3 id="21-타입-가드의-기본-예시">2.1 타입 가드의 기본 예시</h3>
<p>아래는 <code>typeof</code>를 사용하여 <code>unknown</code> 타입을 <code>string</code>으로 좁히는 예제</p>
<pre><code class="language-tsx">let value: unknown = &quot;hi&quot;;

if (typeof value === &quot;string&quot;) {
  // value가 string 타입으로 좁혀짐
  console.log(value.toUpperCase()); // HI
}</code></pre>
<h2 id="3-널-병합-연산자와-옵셔널-체이닝">3. 널 병합 연산자와 옵셔널 체이닝</h2>
<p>타입 단언과 타입 가드 외에도 <strong>널 병합 연산자</strong>와 <strong>옵셔널 체이닝</strong>은 코드의 안정성을 높이는 데 유용함</p>
<h3 id="31-널-병합-연산자-">3.1 널 병합 연산자 (<code>??</code>)</h3>
<p>널 병합 연산자는 값이 <code>null</code> 또는 <code>undefined</code>일 때 <strong>대체값을 제공</strong></p>
<pre><code class="language-tsx">let foo: string | null = null;

// null 또는 undefined일 경우 &quot;default value&quot; 사용
//널 병합 연산자는 null or undefined만 체크
let foo2 = foo ?? &quot;default value&quot;;

console.log(foo2); // &quot;default value&quot; 전송됨</code></pre>
<blockquote>
<p>💡 실행 결과: foo가 null이므로 &quot;default value&quot; 출력</p>
</blockquote>
<h3 id="32-옵셔널-체이닝-">3.2 옵셔널 체이닝 (<code>?.</code>)</h3>
<p>옵셔널 체이닝은 객체의 특정 속성이나 메서드에 접근할 때 <strong>해당 값이 존재하는지 확인</strong>한 뒤 접근하도록 도움</p>
<pre><code class="language-tsx">function printUser(user: { name: string; age?: number } | null) {
    // console.log(user.name); //❌ 에러: 값이 null일 수도 있음
    console.log(user?.name); //✅ 해결: 옵셔널체이닝
}

let user = { name: &quot;james&quot; };
printUser(user); // &quot;james&quot;</code></pre>
<blockquote>
<p>💡 실행 결과: &quot;james&quot; 출력. user가 null일 경우 아무 것도 출력되지 않음</p>
</blockquote>
<table>
<thead>
<tr>
<th>특성</th>
<th>타입 단언</th>
<th>타입 가드</th>
</tr>
</thead>
<tbody><tr>
<td>사용 문법</td>
<td>타입스크립트</td>
<td>자바스크립트</td>
</tr>
<tr>
<td>정의</td>
<td>개발자가 타입스크립트에게 타입을 직접 알려주는 기능</td>
<td>조건문을 사용하여 런타임에 타입을 좁히는 기능</td>
</tr>
<tr>
<td>사용 시점</td>
<td>컴파일 시(정적)</td>
<td>런타임 시(동적)</td>
</tr>
<tr>
<td>주요 문법</td>
<td><code>as</code>키워드 또는<code>&lt;&gt;</code>기호</td>
<td><code>typeof</code>,<code>instanceof</code>등의 연산자</td>
</tr>
</tbody></table>
<h3 id="요약">요약</h3>
<ul>
<li><strong>타입 단언 (Type Assertion)</strong>: 타입스크립트보다 개발자가 타입을 더 잘 아는 경우 직접 타입을 지정</li>
<li><strong>타입 가드 (Type Guard)</strong>: 조건문으로 런타임에 타입을 좁혀 안전성을 확보</li>
<li><strong>널 병합 연산자 (<code>??</code>)</strong>: <code>null</code> 또는 <code>undefined</code>일 때 대체값 제공</li>
<li><strong>옵셔널 체이닝 (<code>?.</code>)</strong>: 객체나 메서드 접근 시 값이 있는지 확인 후 안전하게 접근</li>
</ul>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>
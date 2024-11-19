<h2 id="-or-유니온-타입"><strong><code>|</code> (OR): 유니온 타입</strong></h2>
<ul>
<li><strong>특징</strong>: 여러 타입 중 하나 사용 가능</li>
<li><strong>사용 예시</strong>: 하나의 값이 다양한 타입을 가질 수 있을 때 유용</li>
</ul>
<h3 id="예제-1-기본-타입"><strong>예제 1: 기본 타입</strong></h3>
<pre><code class="language-tsx">let value: number | string | boolean = 10;
value = &quot;hello&quot;;
value = true;</code></pre>
<h3 id="예제-2-객체-타입"><strong>예제 2: 객체 타입</strong></h3>
<pre><code class="language-tsx">let obj: { name: string; age: number } | { skill: string } = {
    name: &quot;Alice&quot;,
    age: 30,
};
obj = { skill: &quot;JavaScript&quot; };</code></pre>
<h3 id="예제-3-배열-타입"><strong>예제 3: 배열 타입</strong></h3>
<pre><code class="language-tsx">let arr: number[] | string[] = [1, 2, 3];
arr = [&quot;apple&quot;, &quot;banana&quot;, &quot;orange&quot;];

// 혼합 배열: 각 요소가 숫자 또는 문자열
let mixArr: (number | string)[] = [&quot;a&quot;, 1, &quot;b&quot;];</code></pre>
<hr />
<h2 id="and-인터섹션-타입"><strong><code>&amp;</code> (AND): 인터섹션 타입</strong></h2>
<ul>
<li><strong>특징</strong>: 두 타입의 모든 속성 결합하여 사용 가능</li>
<li><strong>사용 예시</strong>: 여러 <code>객체</code> 타입 결합 시 유용</li>
</ul>
<h3 id="예제-기본-사용"><strong>예제: 기본 사용</strong></h3>
<pre><code class="language-tsx">let value: { name: string; age: number } &amp; { skill: string } = {
    name: &quot;Alice&quot;,
    age: 30,
    skill: &quot;JavaScript&quot;,
};</code></pre>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>
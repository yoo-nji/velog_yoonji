<p><strong>함수의 타입 지정</strong>: 매개변수와 반환값의 타입을 명확히 지정하는 것</p>
<hr />
<h2 id="함수-선언문과-함수-표현식"><strong>함수 선언문과 함수 표현식</strong></h2>
<h3 id="함수-선언문"><strong>함수 선언문</strong></h3>
<ul>
<li>함수의 이름과 매개변수 타입, 반환 타입을 명시</li>
</ul>
<pre><code class="language-tsx">function greet(name: string): string {
    return `Hello, ${name}!`;
}</code></pre>
<h3 id="함수-표현식"><strong>함수 표현식</strong></h3>
<ul>
<li>익명 함수 또는 이름이 있는 함수로 표현</li>
</ul>
<pre><code class="language-tsx">const expr = function (name: string): string {
    return `Hello, ${name}!`;
};</code></pre>
<p><strong>화살표 함수</strong></p>
<ul>
<li>간결한 문법으로 함수 표현을 줄이는 방법</li>
</ul>
<pre><code class="language-tsx">const exprArrow = (name: string): string =&gt; `Hello, ${name}!`;</code></pre>
<p><strong>함수 타입 지정</strong></p>
<ul>
<li>함수 표현식에서 타입을 명시적으로 지정하는 방법</li>
</ul>
<pre><code class="language-tsx">const expr2: (name: string) =&gt; string = function (name) {
    return `Hello, ${name}!`;
};</code></pre>
<hr />
<h2 id="반환값이-없는-함수-void-타입"><strong>반환값이 없는 함수 (void 타입)</strong></h2>
<p><code>void</code>는 <strong>리턴값이 없는 함수</strong></p>
<pre><code class="language-tsx">function greet(name: string): void {
    console.log(`Hello, ${name}!`);
}

const expr = function (name: string): void {
    console.log(`Hello, ${name}!`);
};

const exprArrow = (name: string): void =&gt; console.log(`Hello, ${name}!`);</code></pre>
<h2 id="매개변수의-기본값과-옵셔널"><strong>매개변수의 기본값과 옵셔널</strong></h2>
<h3 id="옵셔널-매개변수"><strong>옵셔널 매개변수</strong></h3>
<ul>
<li><code>?</code>를 사용해 선택적으로 매개변수를 받는 방법</li>
</ul>
<pre><code class="language-tsx">function sum(n1: number, n2?: number): number {
    return n1 + (n2 || 0);
}
sum(10); // n2는 기본값 0으로 처리</code></pre>
<h3 id="기본값-매개변수"><strong>기본값 매개변수</strong></h3>
<ul>
<li>매개변수에 기본값을 설정하는 방법</li>
</ul>
<pre><code class="language-tsx">function sum(n1: number, n2: number = 0): number {
    return n1 + n2;
}</code></pre>
<hr />
<h2 id="나머지-매개변수-rest-parameters"><strong>나머지 매개변수 (Rest Parameters)</strong></h2>
<h3 id="숫자-타입-예제"><strong>숫자 타입 예제</strong></h3>
<pre><code class="language-tsx">function sum(...rest: number[]): void {
    console.log(rest);
}
sum(1, 2, 3, 4, 5);</code></pre>
<h3 id="여러-타입을-받을-경우"><strong>여러 타입을 받을 경우</strong></h3>
<ul>
<li>튜플을 사용해 각 매개변수의 타입을 지정하는 방법</li>
</ul>
<pre><code class="language-tsx">function printValue(...rest: [number, string, number, string]): void {
    console.log(rest);
}
printValue(1, &quot;a&quot;, 2, &quot;b&quot;);</code></pre>
<hr />
<h2 id="콜백-함수와-타입-지정"><strong>콜백 함수와 타입 지정</strong></h2>
<h3 id="콜백-함수"><strong>콜백 함수</strong></h3>
<ul>
<li>콜백 함수의 매개변수와 반환값에도 타입을 지정하는 방법</li>
</ul>
<pre><code class="language-tsx">const printUser = (callback: (name: string) =&gt; void): void =&gt; {
    callback(&quot;John&quot;);
};

printUser((name) =&gt; {
    console.log(name);
});</code></pre>
<h3 id="콜백-함수와-조건-처리"><strong>콜백 함수와 조건 처리</strong></h3>
<pre><code class="language-tsx">function compareNumbers(
    n1: number,
    n2: number,
    callback: (result: string) =&gt; void
): void {
    if (n1 === n2) {
        callback(&quot;equal&quot;);
    } else {
        callback(&quot;not equal&quot;);
    }
}

compareNumbers(10, 20, (result) =&gt; {
    console.log(`The numbers are ${result}`);
});</code></pre>
<hr />
<h2 id="반환값이-함수인-경우"><strong>반환값이 함수인 경우</strong></h2>
<p>함수의 반환값으로 또 다른 함수를 반환 가능. 이런 패턴은 <strong>클로저</strong>에서 많이 사용</p>
<pre><code class="language-tsx">function createMultiplier(factor: number): (num: number) =&gt; number {
    return (num) =&gt; num * factor;
}

const func = createMultiplier(10);
console.log(func(5)); // 50</code></pre>
<hr />
<h2 id="never-타입"><strong>never 타입</strong></h2>
<p><code>never</code>는 <strong>절대 반환되지 않는 함수</strong>를 나타냄. 예를 들어, <strong>무한 루프</strong>나 <strong>에러를 던지는 함수</strong>에 사용</p>
<pre><code class="language-tsx">function errorFunc(message: string): never {
    throw new Error(message);
}</code></pre>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>
<h3 id="map-메서드와-반복-렌더링"><code>map</code> 메서드와 반복 렌더링</h3>
<p><code>map</code> 메서드는 <strong>배열의 요소를 순회하며 새로운 배열을 반환</strong>하는 역할을 함</p>
<p>리액트에서 자주 사용되는 이유는 <strong>JSX 요소를 배열 데이터로부터 생성</strong>하는 작업에 매우 적합하기 때문임</p>
<hr />
<h3 id="map-메서드의-특징"><code>map</code> 메서드의 특징</h3>
<ol>
<li><strong>콜백 함수 실행</strong>: 배열의 각 요소를 순회하며 콜백 함수 실행</li>
<li><strong>새로운 배열 생성</strong>: 콜백 함수의 반환값으로 구성된 <strong>새로운 배열</strong> 생성</li>
<li><strong>원본 배열 불변</strong>: 원본 배열 유지</li>
</ol>
<hr />
<h3 id="리액트에서의-활용">리액트에서의 활용</h3>
<p>리액트에서는 <code>map</code> 메서드를 사용해 <strong><code>배열</code></strong> 데이터를 <strong>JSX 요소로 변환</strong>하여 <strong>반복 렌더링</strong>이 가능함</p>
<blockquote>
<p>💡 표현식({})에서 객체는 직접 출력이 불가능하며, JSON.stringify()를 사용하여 문자열로 변환해야 함</p>
</blockquote>
<p><strong>예시</strong></p>
<pre><code class="language-tsx">export default function Loop() {
  // 배열 데이터 생성
  const items = [&quot;apple&quot;, &quot;banana&quot;, &quot;cherry&quot;];
  return (
    &lt;ul&gt;
      {items.map((item) =&gt; {
        return &lt;li&gt;{item}&lt;/li&gt;;
      })}
    &lt;/ul&gt;
  );
}</code></pre>
<p><strong>실행 결과</strong></p>
<pre><code class="language-html">&lt;ul&gt;
  &lt;li&gt;apple&lt;/li&gt;
  &lt;li&gt;banana&lt;/li&gt;
  &lt;li&gt;cherry&lt;/li&gt;
&lt;/ul&gt;</code></pre>
<hr />
<h3 id="map-메서드의-매개변수"><code>map</code> 메서드의 매개변수</h3>
<p><code>map</code> 메서드는 3개의 매개변수를 받을 수 있음:</p>
<ol>
<li><code>item</code>: 현재 처리 중인 요소 (필수)</li>
<li><code>index</code>: 현재 처리 중인 요소의 인덱스 (선택)</li>
<li><code>array</code>: <code>map</code>을 호출한 배열 자체 (선택)</li>
</ol>
<p><strong>예시: <code>item</code>과 <code>index</code> 사용</strong></p>
<pre><code class="language-tsx">export default function LoopWithIndex() {
  const items = [&quot;apple&quot;, &quot;banana&quot;, &quot;cherry&quot;];
  return (
    &lt;ul&gt;
      {items.map((item, index) =&gt; (
        &lt;li key={index}&gt;{`${index + 1}. ${item}`}&lt;/li&gt;
      ))}
    &lt;/ul&gt;
  );
}</code></pre>
<p><strong>실행 결과</strong></p>
<pre><code class="language-html">&lt;ul&gt;
  &lt;li&gt;1. apple&lt;/li&gt;
  &lt;li&gt;2. banana&lt;/li&gt;
  &lt;li&gt;3. cherry&lt;/li&gt;
&lt;/ul&gt;</code></pre>
<hr />
<h3 id="key-속성"><code>key</code> 속성</h3>
<p>리액트에서 반복 렌더링할 때는 각 요소에 <strong>고유한 <code>key</code> 속성</strong>을 지정해야 함</p>
<p><strong>key 역할</strong></p>
<ol>
<li><strong>렌더링 성능 최적화</strong>: 변경된 요소를 효율적으로 업데이트</li>
<li><strong>요소 추적</strong>: 요소를 정확히 식별</li>
</ol>
<h3 id="key-설정-예시"><code>key</code> 설정 예시</h3>
<pre><code class="language-tsx">export default function LoopWithKey() {
  const items = [&quot;apple&quot;, &quot;banana&quot;, &quot;cherry&quot;];
  return (
    &lt;ul&gt;
      {items.map((item, index) =&gt; (
        &lt;li key={index}&gt;{item}&lt;/li&gt;
      ))}
    &lt;/ul&gt;
  );
}</code></pre>
<blockquote>
<p>💡 주의: 배열의 인덱스를 key로 사용하는 것은 권장되지 않음. 데이터에 고유한 값(ID)이 있다면 이를 사용할 것</p>
</blockquote>
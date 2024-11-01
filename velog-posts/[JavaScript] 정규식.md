<p>정규식(Regular Expressions)은 텍스트 데이터에서 특정 패턴을 찾거나 수정하는 데 사용됨. 자바스크립트에서는 정규식을 통해 문자 검색, 대체, 유효성 검사 등을 쉽게 수행 가능</p>
<hr />
<h2 id="기본-구조-패턴플래그">기본 구조: <code>/패턴/플래그</code></h2>
<ul>
<li><strong>패턴</strong>: 찾고자 하는 문자열이나 문자 조합</li>
<li><strong>플래그</strong>: 패턴의 검색 방식을 설정하는 옵션</li>
</ul>
<p>정규식의 기본 구조는 <code>/패턴/플래그</code> 형식을 따름. 패턴은 찾고자 하는 문자열을 나타내고, 플래그는 검색 조건을 지정함</p>
<h2 id="주요-플래그-설명">주요 플래그 설명</h2>
<p>자바스크립트에서 자주 사용하는 주요 플래그:</p>
<ul>
<li><strong>g</strong> (global): 문자열 내 <strong>모든</strong> 일치 항목을 찾음<ul>
<li>예: <code>/ain/g</code>는 &quot;ain&quot;이 포함된 모든 문자열을 찾음</li>
<li><strong>g</strong> 플래그가 없으면 첫 번째로 일치하는 항목만 반환</li>
</ul>
</li>
<li><strong>i</strong> (case-insensitive): <strong>대소문자를 구분하지 않고</strong> 검색<ul>
<li>예: <code>/cat/i</code>는 &quot;cat&quot;, &quot;Cat&quot;, &quot;CAT&quot; 등의 모든 대소문자 조합을 찾음</li>
<li>대소문자를 구분하지 않아야 할 경우 유용하게 사용 가능</li>
</ul>
</li>
</ul>
<h3 id="플래그-조합-사용-예시">플래그 조합 사용 예시</h3>
<p>플래그는 하나 이상 동시에 사용 가능하여 더 세밀한 검색이 가능함</p>
<pre><code class="language-jsx">const text = &quot;Cat, cat, CAT&quot;;
const pattern = /cat/gi;
const matches = text.match(pattern);
console.log(matches); // Output: [&quot;Cat&quot;, &quot;cat&quot;, &quot;CAT&quot;]</code></pre>
<p>위 예제에서는 <code>/cat/gi</code>를 사용하여 대소문자 구분 없이 문자열 내 &quot;cat&quot;이 등장하는 모든 항목을 찾음</p>
<h2 id="활용법">활용법</h2>
<pre><code class="language-jsx">const text = &quot;The cat and the hat&quot;;
const pattern = /at/g;

// 특정 패턴('at')을 전역 검색하여 모든 일치 항목을 배열로 반환
const matches = text.match(pattern);
console.log(matches); // Output: [&quot;at&quot;, &quot;at&quot;]

// 정규식을 사용하여 모든 'at' 패턴을 'AT'로 대체
const newText = text.replace(pattern, &quot;AT&quot;);
console.log(newText); // Output: &quot;The cAT and the hAT&quot;</code></pre>
<ol>
<li><code>match()</code> 메서드를 사용해 &quot;at&quot;이 포함된 모든 문자열을 검색하여 배열로 반환</li>
<li><code>replace()</code> 메서드를 통해 &quot;at&quot;을 &quot;AT&quot;로 대체</li>
</ol>
<h3 id="자주-사용하는-정규식-패턴">자주 사용하는 정규식 패턴</h3>
<table>
<thead>
<tr>
<th>패턴</th>
<th>설명</th>
<th>예시 (패턴)</th>
</tr>
</thead>
<tbody><tr>
<td><code>.</code></td>
<td>임의의 한 문자와 일치</td>
<td><code>/c.t/</code></td>
</tr>
<tr>
<td><code>\d</code></td>
<td>숫자와 일치</td>
<td><code>/\d/</code></td>
</tr>
<tr>
<td><code>\w</code></td>
<td>알파벳, 숫자, 언더바(_)와 일치</td>
<td><code>/\w/</code></td>
</tr>
<tr>
<td><code>\s</code></td>
<td>공백 문자와 일치</td>
<td><code>/\s/</code></td>
</tr>
<tr>
<td><code>^</code></td>
<td>문자열의 시작에 일치</td>
<td><code>/^The/</code></td>
</tr>
<tr>
<td><code>$</code></td>
<td>문자열의 끝에 일치</td>
<td><code>/end$/</code></td>
</tr>
<tr>
<td><code>*</code></td>
<td>앞 문자가 0회 이상 반복</td>
<td><code>/he*/</code></td>
</tr>
<tr>
<td><code>+</code></td>
<td>앞 문자가 1회 이상 반복</td>
<td><code>/he+/</code></td>
</tr>
<tr>
<td><code>{n}</code></td>
<td>앞 문자가 정확히 n회 반복</td>
<td><code>/a{3}/</code></td>
</tr>
<tr>
<td><code>{n,}</code></td>
<td>앞 문자가 최소 n회 반복</td>
<td><code>/a{2,}/</code></td>
</tr>
<tr>
<td><code>[]</code></td>
<td>대괄호 안의 문자들 중 하나와 일치</td>
<td><code>/[aeiou]/</code></td>
</tr>
<tr>
<td><code>()</code></td>
<td>그룹으로 묶어 하나의 단위로 사용 가능</td>
<td><code>/(abc)/</code></td>
</tr>
</tbody></table>
<h2 id="✅-마치며">✅ 마치며</h2>
<p><strong>정규식은 외우기보다 참고하며 사용하기</strong></p>
<p>자주 사용하지 않는 패턴은 필요할 때 검색이나 참고 자료를 활용하도록 하자(gpt 👍)</p>
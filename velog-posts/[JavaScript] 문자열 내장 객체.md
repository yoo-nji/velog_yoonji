<h3 id="1-length"><strong>1. <code>length</code></strong></h3>
<p>문자열의 길이 반환</p>
<pre><code class="language-jsx">const str = &quot;Hello, world!&quot;;
console.log(str.length); // 13</code></pre>
<h3 id="2-charatindex"><strong>2. <code>charAt(index)</code></strong></h3>
<p>주어진 인덱스 번호의 문자 반환</p>
<pre><code class="language-jsx">const str = &quot;Hello&quot;;
console.log(str.charAt(1)); // 'e'

//문자열은 유사 배열이기 때문에 배열처럼 인덱스로 접근 가능
console.log(str[1]); // 'e'</code></pre>
<h3 id="3-indexofstring-⭐️"><strong>3. <code>indexOf(string)</code></strong> ⭐️</h3>
<p>지정된 문자열이 처음 등장하는 위치의 인덱스 반환. 찾지 못하면 <code>-1</code> 반환</p>
<pre><code class="language-jsx">const str = &quot;Hello, world!&quot;;
console.log(str.indexOf(&quot;world&quot;)); // 7
console.log(str.indexOf(&quot;JavaScript&quot;)); // -1 (찾지 못함)</code></pre>
<h3 id="4-lastindexofstring"><strong>4. <code>lastIndexOf(string)</code></strong></h3>
<p>지정된 문자열이 마지막으로 나타나는 위치의 인덱스 반환</p>
<pre><code class="language-jsx">const str = &quot;Hello, World! Hello!&quot;;
console.log(str.lastIndexOf(&quot;Hello&quot;)); // 13</code></pre>
<h3 id="5-substringstart-end"><strong>5. <code>substring(start, end)</code></strong></h3>
<p>주어진 범위 내의 문자열 반환. <code>start</code>부터 <code>end</code> 전까지 추출, 음수 사용 불가</p>
<pre><code class="language-jsx">const str = &quot;Hello, world!&quot;;
console.log(str.substring(0, 5)); // &quot;Hello&quot;
console.log(str.substring(7)); // &quot;world!&quot;</code></pre>
<h3 id="6-slicestart-end"><strong>6. <code>slice(start, end)</code></strong></h3>
<p>주어진 인덱스를 기준으로 문자열을 잘라 반환. 음수 인덱스 사용 가능 ⇒ substring보다 유연함</p>
<pre><code class="language-jsx">const str = &quot;Hello, world!&quot;;
console.log(str.slice(-6, -1)); // &quot;world&quot;
console.log(str.slice(7)); // &quot;world!&quot;
console.log(str.slice(0, 5)); // &quot;Hello&quot;</code></pre>
<p><strong>반환값</strong>: 지정된 범위의 부분 문자열 (문자열)</p>
<h3 id="7-tolowercase-⭐️"><strong>7. <code>toLowerCase()</code></strong> ⭐️</h3>
<p>문자열을 소문자로 변환하여 반환</p>
<pre><code class="language-jsx">const str = &quot;HELLO&quot;;
console.log(str.toLowerCase()); // &quot;hello&quot;</code></pre>
<p><strong>반환값</strong>: 소문자로 변환된 문자열</p>
<h3 id="8-touppercase-⭐️"><strong>8. <code>toUpperCase()</code></strong> ⭐️</h3>
<p>문자열을 대문자로 변환하여 반환</p>
<pre><code class="language-jsx">const str = &quot;hello&quot;;
console.log(str.toUpperCase()); // &quot;HELLO&quot;</code></pre>
<p><strong>반환값</strong>: 대문자로 변환된 문자열</p>
<h3 id="9-trim-⭐️⭐️"><strong>9. <code>trim()</code></strong> ⭐️⭐️</h3>
<p>문자열 양쪽의 공백을 제거하고 반환</p>
<p>사용: 사용자 입력 요소 제어할 때 많이 사용(ex. 로그인 인풋 공백)</p>
<pre><code class="language-jsx">const str = &quot;   Hello, world!   &quot;;
console.log(str.trim()); // &quot;Hello, world!&quot;</code></pre>
<p><strong>반환값</strong>: 양쪽 공백이 제거된 문자열</p>
<h3 id="10-splitseparator"><strong>10. <code>split(separator)</code></strong></h3>
<p>주어진 구분자를 기준으로 문자열을 분할하여 배열로 반환</p>
<pre><code class="language-jsx">const str = &quot;사과,바나나,체리&quot;;
console.log(str.split(&quot;,&quot;)); // [&quot;사과&quot;, &quot;바나나&quot;, &quot;체리&quot;]

// 공백으로 문장 분할
const 문장 = &quot;안녕하세요 여러분! 오늘 기분이 어떠신가요?&quot;;
console.log(문장.split(&quot; &quot;)); // [&quot;안녕하세요&quot;, &quot;여러분!&quot;, &quot;오늘&quot;, &quot;기분이&quot;, &quot;어떠신가요?&quot;]</code></pre>
<p><strong>반환값</strong>: 문자열을 분할한 배열</p>
<h3 id="11-replacestring-replacement"><strong>11. <code>replace(string, replacement)</code></strong></h3>
<p>지정된 문자열을 다른 문자열로 <strong>한 번만</strong> 교체하고 반환함</p>
<pre><code class="language-jsx">const str = &quot;Hello, world!&quot;;
console.log(str.replace(&quot;world&quot;, &quot;JavaScript&quot;)); // &quot;Hello, JavaScript!&quot;</code></pre>
<ul>
<li><strong>반환값</strong>: 교체된 문자열</li>
</ul>
<h3 id="12-replaceallstring-replacement"><strong>12. <code>replaceAll(string, replacement)</code></strong></h3>
<p>지정된 문자열을 <strong>모두</strong> 찾아 다른 문자열로 교체하고 반환함</p>
<pre><code class="language-jsx">const str = &quot;apple, apple, apple&quot;;
console.log(str.replaceAll(&quot;apple&quot;, &quot;orange&quot;)); // &quot;orange, orange, orange&quot;</code></pre>
<ul>
<li><strong>반환값</strong>: 모든 항목이 교체된 문자열</li>
</ul>
<h3 id="13-includesstring-⭐️⭐️"><strong>13. <code>includes(string)</code></strong>: ⭐️⭐️</h3>
<p>문자열이 포함되어 있으면 <code>true</code>, 아니면 <code>false</code>를 반환함</p>
<pre><code class="language-jsx">const str = &quot;Hello, world!&quot;;
console.log(str.includes(&quot;world&quot;)); // true
console.log(str.includes(&quot;JavaScript&quot;)); // false</code></pre>
<ul>
<li><strong>반환값</strong>: <code>true</code> 또는 <code>false</code></li>
</ul>
<h3 id="14-startswithstring"><strong>14. <code>startsWith(string)</code></strong></h3>
<p>문자열이 지정된 문자열로 시작하면 <code>true</code>를 반환함 ⭐️</p>
<pre><code class="language-jsx">const str = &quot;Hello, world!&quot;;
console.log(str.startsWith(&quot;Hello&quot;)); // true</code></pre>
<ul>
<li><strong>반환값</strong>: <code>true</code> 또는 <code>false</code></li>
</ul>
<h3 id="15-endswithstring"><strong>15. <code>endsWith(string)</code></strong></h3>
<p>문자열이 지정된 문자열로 끝나면 <code>true</code>를 반환함</p>
<pre><code class="language-jsx">const str = &quot;Hello, world!&quot;;
console.log(str.endsWith(&quot;!&quot;)); // true</code></pre>
<ul>
<li><strong>반환값</strong>: <code>true</code> 또는 <code>false</code></li>
</ul>
<h3 id="16-repeatcount"><strong>16. <code>repeat(count)</code></strong></h3>
<p>문자열을 지정한 횟수만큼 반복하여 반환함</p>
<pre><code class="language-jsx">const str = &quot;*&quot;;
console.log(str.repeat(5)); // &quot;*****&quot;</code></pre>
<ul>
<li><strong>반환값</strong>: 반복된 문자열</li>
</ul>
<h3 id="17-localecomparestring"><strong>17. <code>localeCompare(string)</code></strong></h3>
<p>두 문자열을 비교하여 음수, 0, 양수를 반환함</p>
<ul>
<li><strong>음수 (-1)</strong>: 비교하는 문자열이 인자로 전달된 문자열보다 사전적으로 앞에 올 때</li>
<li><strong>0</strong>: 두 문자열이 동일할 때</li>
<li><strong>양수 (1)</strong>: 비교하는 문자열이 인자로 전달된 문자열보다 사전적으로 뒤에 올 때</li>
</ul>
<pre><code class="language-jsx">const str1 = &quot;a&quot;;
const str2 = &quot;b&quot;;
console.log(str1.localeCompare(str2)); // -1</code></pre>
<ul>
<li><strong>반환값</strong>: 비교 결과 (<code>-1</code>, <code>0</code>, <code>1</code>)</li>
</ul>
<h3 id="18-matchregex"><strong>18. <code>match(regex)</code></strong></h3>
<p>정규 표현식과 일치하는 부분을 찾아 배열로 반환하고, 없으면 <code>null</code>을 반환함</p>
<pre><code class="language-jsx">const text = &quot;The rain in Spain&quot;;
const matches = text.match(/ain/g);
console.log(matches); // [&quot;ain&quot;, &quot;ain&quot;]</code></pre>
<ul>
<li><strong>반환값</strong>: 일치하는 부분의 배열 또는 <code>null</code></li>
</ul>
<h3 id="19-searchregex"><strong>19. <code>search(regex)</code></strong></h3>
<p>정규 표현식과 일치하는 첫 번째 위치의 인덱스를 반환하며, 없으면 <code>-1</code>을 반환함</p>
<pre><code class="language-jsx">const text = &quot;The rain in Spain&quot;;
console.log(text.search(/ain/)); // 5</code></pre>
<ul>
<li><strong>반환값</strong>: 첫 일치 항목의 인덱스 또는 <code>-1</code></li>
</ul>
<h3 id="20-padstartlength-string"><strong>20. <code>padStart(length, string)</code></strong></h3>
<p>지정한 길이까지 앞쪽을 특정 문자로 채운 문자열을 반환함</p>
<pre><code class="language-jsx">const str = &quot;42&quot;;
console.log(str.padStart(5, &quot;0&quot;)); // &quot;00042&quot;</code></pre>
<ul>
<li><strong>반환값</strong>: 지정된 길이만큼 채워진 문자열</li>
</ul>
<h3 id="21-padendlength-string"><strong>21. <code>padEnd(length, string)</code></strong></h3>
<p>지정한 길이까지 뒤쪽을 특정 문자로 채운 문자열을 반환함</p>
<pre><code class="language-jsx">const str = &quot;42&quot;;
console.log(str.padEnd(5, &quot;0&quot;)); // &quot;42000&quot;</code></pre>
<ul>
<li><strong>반환값</strong>: 지정된 길이만큼 채워진 문자열</li>
</ul>
<h3 id="22-tolocaleuppercase"><strong>22. <code>toLocaleUpperCase()</code></strong></h3>
<p>지역 설정에 따라 대문자로 변환된 문자열을 반환함</p>
<h3 id="23-tolocalelowercase"><strong>23. <code>toLocaleLowerCase()</code></strong></h3>
<p>지역 설정에 따라 소문자로 변환된 문자열을 반환함</p>
<h3 id="24-valueof"><strong>24. <code>valueOf()</code></strong></h3>
<p>문자열 객체의 원시 값을 반환함</p>
<pre><code class="language-jsx">const strObj = new String(&quot;Hello&quot;);
console.log(strObj.valueOf()); // &quot;Hello&quot;</code></pre>
<ul>
<li><strong>반환값</strong>: 문자열의 원시 값</li>
</ul>
<blockquote>
<p>📚 자세한 건 <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String">MDN 공식 문서</a> 참고</p>
</blockquote>
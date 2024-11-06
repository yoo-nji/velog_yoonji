<h2 id="📍-문제">📍 문제</h2>
<p>프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.</p>
<p>전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 <code>*</code>으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.</p>
<h3 id="제한-조건">제한 조건</h3>
<ul>
<li>phone_number는 길이 4 이상, 20이하인 문자열입니다.</li>
</ul>
<h3 id="입출력-예">입출력 예</h3>
<table>
<thead>
<tr>
<th>phone_number</th>
<th>return</th>
</tr>
</thead>
<tbody><tr>
<td>&quot;01033334444&quot;</td>
<td>&quot;<strong>***</strong>4444&quot;</td>
</tr>
<tr>
<td>&quot;027778888&quot;</td>
<td>&quot;*****8888&quot;</td>
</tr>
</tbody></table>
<h2 id="🥔-내-코드">🥔 내 코드</h2>
<p>1차</p>
<pre><code class="language-jsx">function solution(phone_number) {
  let number = &quot;&quot;;
  let result = phone_number.length - 4;
  for (let i = 0; i &lt; phone_number.length; i++) {
    if (i &lt; result) {
      number += &quot;*&quot;;
    } else number += phone_number[i];
  } return number;
}</code></pre>
<p>2차: 코드 개선 - if문을 삼항 연산자로 변경</p>
<pre><code class="language-jsx">function solution(phone_number) {
  let number = &quot;&quot;;
  let result = phone_number.length - 4;
  for (let i = 0; i &lt; phone_number.length; i++) {
    number = i &lt; result ? number += &quot;*&quot; : number += phone_number[i];
  }
  return number;
}</code></pre>
<h2 id="✅-풀이-과정">✅ 풀이 과정</h2>
<ol>
<li>number라는 빈 문자열을 선언합니다.</li>
<li>result에 전화번호 길이에서 4를 뺀 값을 할당합니다. 이는 '*'로 가릴 문자의 개수입니다.</li>
<li>전화번호의 길이만큼 반복문을 실행합니다:</li>
</ol>
<ul>
<li>인덱스가 result보다 작으면 (뒤에서 4자리 전까지) number에 '*'를 추가합니다.</li>
<li>그렇지 않으면 (뒤 4자리) 원래 전화번호의 숫자를 그대로 추가합니다.</li>
</ul>
<ol>
<li>최종적으로 변환된 number 문자열을 반환합니다.</li>
</ol>
<h2 id="💡-다른-사람의-코드">💡 다른 사람의 코드</h2>
<pre><code class="language-jsx">function solution(phone_number) {
   let result = []

   for(let i = 0; i &lt; phone_number.length; i++){
      if(i &lt; phone_number.length-4){
          result.push('*')
      } else {
          result.push(phone_number[i])
      }
   }

   return result.join('')
}</code></pre>
<h2 id="💬-마치며">💬 마치며</h2>
<p>이 풀이는 내 방식과 거의 비슷하지만, 빈 배열을 생성하여 요소를 push하고 <code>.join()</code> 메서드를 사용해 배열의 모든 요소를 하나의 문자열로 연결할 수 있다는 점을 새롭게 알게 되었다.</p>
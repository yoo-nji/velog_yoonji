<h2 id="📍-문제">📍 문제</h2>
<p>피보나치 수는 F(0) = 0, F(1) = 1일 때, 1 이상의 n에 대하여 F(n) = F(n-1) + F(n-2) 가 적용되는 수 입니다.</p>
<p>예를들어</p>
<ul>
<li>F(2) = F(0) + F(1) = 0 + 1 = 1</li>
<li>F(3) = F(1) + F(2) = 1 + 1 = 2</li>
<li>F(4) = F(2) + F(3) = 1 + 2 = 3</li>
<li>F(5) = F(3) + F(4) = 2 + 3 = 5</li>
</ul>
<p>와 같이 이어집니다.</p>
<p>2 이상의 n이 입력되었을 때, n번째 피보나치 수를 1234567으로 나눈 나머지를 리턴하는 함수, solution을 완성해 주세요.</p>
<h3 id="제한-사항">제한 사항</h3>
<ul>
<li>n은 2 이상 100,000 이하인 자연수입니다.</li>
</ul>
<h3 id="입출력-예">입출력 예</h3>
<table>
<thead>
<tr>
<th>n</th>
<th>return</th>
</tr>
</thead>
<tbody><tr>
<td>3</td>
<td>2</td>
</tr>
<tr>
<td>5</td>
<td>5</td>
</tr>
</tbody></table>
<h3 id="입출력-예-설명">입출력 예 설명</h3>
<p>피보나치수는 0번째부터 0, 1, 1, 2, 3, 5, ... 와 같이 이어집니다.</p>
<h2 id="🥔-내-코드">🥔 내 코드</h2>
<p>1차 - 실패 (숫자가 너무 커져서 오버플로우 발생) ❌</p>
<pre><code class="language-jsx">function solution(n) {
let a = 0;
let b = 1;
let temp = null;
let arr = []
for(let i = 0 ; i &lt;= n ; ++i){
  arr.push(a);
  temp = a;
  a = b;
  b = temp + a
} return arr.pop() % 1234567
}</code></pre>
<p><strong>풀이</strong></p>
<ul>
<li>변수 <code>a</code>와 <code>b</code>를 선언하고 각각 0과 1로 초기화</li>
<li><code>temp</code> 변수를 선언하여 임시 저장소로 사용</li>
<li>빈 배열 <code>arr</code> 생성</li>
<li>반복문을 통해 <code>n</code>까지 순회하면서:</li>
<li>배열에 <code>a</code>값을 추가</li>
<li><code>temp</code>에 <code>a</code>값을 임시 저장</li>
<li><code>a</code>에 <code>b</code>값을 할당</li>
<li><code>b</code>에 <code>temp + a</code> 값을 할당하여 다음 피보나치 수 계산</li>
<li>마지막으로 배열의 마지막 값을 꺼내서 1234567로 나눈 나머지를 반환</li>
</ul>
<p>2차 - 실패 (오버플로우) ❌</p>
<pre><code class="language-tsx">function solution(n) {
let arr = [0, 1]
for(let i = 0 ; i &lt;= n - 2 ; i++){
    arr.push(arr[i] + arr[i + 1])
} return arr.pop() % 1234567
} </code></pre>
<p>풀이(배열 활용)</p>
<ul>
<li>초기값으로 [0, 1]이 담긴 배열 생성</li>
<li>n-2만큼 반복하면서 이전 두 수를 더한 값을 배열에 추가</li>
<li>마지막으로 배열의 마지막 값을 꺼내서 1234567로 나눈 나머지를 반환</li>
</ul>
<p>3차 - 실패 (오버플로우) ❌</p>
<pre><code class="language-tsx">function solution(n) {
let arr = [0, 1]
for(let i = 2 ; i &lt;= n ; i++){
    arr[i] =  arr[i - 1] + arr[i - 2]
} return arr[n] % 1234567
} </code></pre>
<p>풀이(배열 인덱스 활용)</p>
<ul>
<li>배열의 0번째와 1번째 인덱스에 초기값 [0, 1] 할당</li>
<li>2부터 n까지 반복하면서 i번째 인덱스에 이전 두 수의 합을 할당</li>
<li>마지막으로 n번째 인덱스의 값을 1234567로 나눈 나머지를 반환</li>
</ul>
<p><strong>4차 성공 🎉</strong></p>
<pre><code class="language-tsx">function solution(n) {
let arr = [0, 1]
for(let i = 2 ; i &lt;= n ; i++){
    arr[i] =  (arr[i - 1] + arr[i - 2]) % 1234567
} return arr[n]
} </code></pre>
<h2 id="💫-실패-이유">💫 실패 이유</h2>
<p>3차까지 테스트7부터 실패가 떠서 아니 대체 왜…를 반복하다가 이런 글을 발견하게 된다</p>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/b183bdc0-6cff-434e-85b8-9f8e510da856/image.png" /></p>
<blockquote>
<p>👽 <strong>요약</strong></p>
<p>일반적인 프로그래밍 언어의 <strong>int 자료형(4byte)</strong>은 -2,147,483,648 ~ 2,147,483,647 범위만 표현 가능</p>
<p>범위를 벗어나면 <strong><code>오버플로우</code></strong>가 발생해 예상치 못한 결과가 나옴</p>
<p>(예: 2,147,483,647 + 1 = -2,147,483,648)</p>
<p>하지만 (A + B) % C = ((A % C) + (B % C)) % C라는 <strong><code>모듈러(나머지) 연산</code></strong> 성질을 이용하면 오버플로우 없이 정확한 결과를 얻을 수 있음</p>
</blockquote>
<p>본문: <a href="https://school.programmers.co.kr/questions/11991">여기</a></p>
<p>즉, 마지막에만 나머지 연산을 수행 시 이미 이전 단계에서 오버플로우가 발생해 잘못된 결과가 나올 수 있음. 따라서 계산 과정 중간중간 나머지 연산을 통해 오버플로우 방지가 필요함</p>
<h2 id="✅-나머지-연산">✅ 나머지 연산</h2>
<p><strong>장점</strong>: 자료형이 엄격한 다른 언어에서도 오버플로우 방지와 연산 시간 단축 가능</p>
<p><strong>공식</strong></p>
<ul>
<li>더하기</li>
</ul>
<pre><code class="language-jsx">(A + B) % M = (A % M + B % M) % M</code></pre>
<ul>
<li>곱하기</li>
</ul>
<pre><code class="language-jsx">(A × B) % M = (A % M × B % M) % M</code></pre>
<ul>
<li>빼기</li>
</ul>
<pre><code class="language-jsx">(A - B) % M = (A % M - B % M + M) % M</code></pre>
<h3 id="최종-답안">최종 답안</h3>
<pre><code class="language-tsx">function solution(n) {
let arr = [0, 1]
for(let i = 2 ; i &lt;= n ; i++){
    arr[i] =  (arr[i - 1] + arr[i - 2]) % 1234567
} return arr[n]
} </code></pre>
<h2 id="💡-다른-사람의-코드">💡 다른 사람의 코드</h2>
<pre><code class="language-jsx">function solution(n) {
   var result = [0 , 1];
   while ( result.length !== n + 1) {
       var fibonacci = (result[result.length - 2] + result[result.length - 1]) % 1234567
       result.push(fibonacci);
   }
    return result[n];
}</code></pre>
<h2 id="💬-마치며">💬 마치며</h2>
<p>피보나치 문제는 데브코스 연습문제로도 풀어봐서 나름 익숙하다고 생각하고 도전했는데, 오버플로우까지 고려해야 할 줄은 몰랐다. 나머지 연산의 활용법도 아직 이해가 잘 안 가서 더 많은 문제를 풀어봐야겠다</p>
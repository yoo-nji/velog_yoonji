<h2 id="📚-til">📚 TIL</h2>
<p><a href="https://velog.io/@yoon_ji/%EC%BB%A8%ED%85%8D%EC%8A%A4%ED%8A%B8%EC%99%80-%ED%98%B8%EC%9D%B4%EC%8A%A4%ED%8C%85">호이스팅과 컨텍스트</a></p>
<h2 id="💡-추가-학습-내용">💡 추가 학습 내용</h2>
<h3 id="자주-사용되는-메서드-리스트">자주 사용되는 메서드 리스트</h3>
<ul>
<li><p><strong><code>reduce()</code></strong>: <strong>배열</strong>의 각 요소에 대해 주어진 리듀서(reducer) 함수를 실행하고, 하나의 결과값을 반환함 (누산메서드, 누적메서드)</p>
<ul>
<li><p>예시코드</p>
<pre><code class="language-jsx">  // 배열의 모든 요소 합계 구하기
  const numbers = [1, 2, 3, 4, 5];
  const sum = numbers.reduce((accumulator, currentValue) =&gt; accumulator + currentValue, 0);
  console.log(sum); // 출력: 15

  // 객체 배열에서 특정 속성의 합계 구하기
  const items = [
    { name: 'Apple', price: 0.5 },
    { name: 'Banana', price: 0.3 },
    { name: 'Orange', price: 0.6 }
  ];
  const totalPrice = items.reduce((total, item) =&gt; total + item.price, 0);
  console.log(totalPrice); // 출력: 1.4</code></pre>
</li>
</ul>
</li>
<li><p><strong><code>replace()</code></strong>: 문자열에서 특정 패턴을 다른 문자열로 대체함</p>
<ul>
<li><p>예시코드</p>
<pre><code class="language-jsx">  // 문자열에서 첫 번째로 발견되는 패턴만 대체
  const str = &quot;Hello, World!&quot;;
  const newStr = str.replace(&quot;o&quot;, &quot;0&quot;);
  console.log(newStr); // 출력: &quot;Hell0, World!&quot;

  // 정규표현식을 사용하여 모든 패턴 대체
  const str2 = &quot;Hello, World!&quot;;
  const newStr2 = str2.replace(/o/g, &quot;0&quot;);
  console.log(newStr2); // 출력: &quot;Hell0, W0rld!&quot;</code></pre>
</li>
</ul>
</li>
<li><p><strong>includes():</strong> 배열이나 문자열에 특정 요소나 부분 문자열이 포함되어 있는지 확인함</p>
<ul>
<li><p>예시 코드</p>
<pre><code class="language-jsx">  // 배열에 특정 요소가 포함되어 있는지 확인
  const arr = [1, 2, 3, 4, 5];
  const num = 3;

  if (arr.includes(num)) {
    console.log(`${num}은 배열에 포함되어 있음`);
  } else {
    console.log(`${num}은 배열에 포함되어 있지 않음`);
  }

  // 문자열에 특정 부분 문자열이 포함되어 있는지 확인
  const str = &quot;Hello, World!&quot;;
  const sub = &quot;World&quot;;

  if (str.includes(sub)) {
    console.log(`&quot;${sub}&quot;는 문자열에 포함되어 있음`);
  } else {
    console.log(`&quot;${sub}&quot;는 문자열에 포함되어 있지 않음`);
  }</code></pre>
</li>
</ul>
</li>
<li><p><strong><code>length</code></strong>: 문자열의 길이를 반환함</p>
</li>
<li><p><strong>toLowerCase():</strong> 문자열을 <code>소문자</code>로 변환함</p>
</li>
<li><p><strong>toUpperCase():</strong> 문자열을 <code>대문자</code>로 변환함</p>
</li>
<li><p><strong>trim():</strong> 문자열의 앞뒤 공백을 제거함</p>
</li>
<li><p><strong><code>split()</code></strong>: 문자열을 특정 구분자로 나누어 배열로 반환함</p>
</li>
<li><p><strong><code>replaceAll()</code></strong>: 문자열 내의 모든 일치하는 부분을 새로운 문자열로 교체함</p>
<ul>
<li><p>예시코드</p>
<pre><code class="language-jsx">  &quot;hello world&quot;.replaceAll(&quot;o&quot;,&quot;&quot;) //o를 찾아서 없앰
  //출력 hell wrld</code></pre>
</li>
</ul>
</li>
<li><p><strong><code>reverse()</code></strong>: 배열이나 문자열의 순서를 반대로 뒤집음</p>
<ul>
<li><p>예시코드</p>
<pre><code class="language-jsx">  // 배열 뒤집기 예제
  const arr = [1, 2, 3, 4, 5];
  const reversed = arr.reverse();

  console.log(reversed);
  // 출력: [5, 4, 3, 2, 1]

  // 문자열 뒤집기 예제
  const str = &quot;Hello, World!&quot;;
  const reversed = str.split('').reverse().join('');

  console.log(reversed);
  // 출력: &quot;!dlroW ,olleH&quot;</code></pre>
<p>  배열의 경우 <code>reverse()</code> 메서드를 직접 사용할 수 있지만, 문자열의 경우 배열로 변환 후 뒤집고 다시 문자열로 결합하는 과정이 필요함</p>
</li>
</ul>
</li>
</ul>
<h3 id="유클리드-호제법">유클리드 호제법</h3>
<p>유클리드 호제법: 최대공약수(GCD) 구하는 알고리즘.</p>
<p>두 수 a와 b의 최대공약수는 b가 0이 될 때까지 a를 b로 나눈 나머지 반복 계산하여 구함</p>
<pre><code class="language-jsx">function gcd(a, b) {
  if (b === 0) return a;
  return gcd(b, a % b);
}

// console.log(gcd(56, 98)); // 14</code></pre>
<h3 id="버블정렬">버블정렬</h3>
<p>버블 정렬: 인접한 두 요소를 비교하여 더 큰 값을 오른쪽으로 이동시키는 간단한 정렬 알고리즘.</p>
<p>배열이 완전히 정렬될 때까지 이 과정 반복</p>
<pre><code class="language-jsx">// 버블 정렬
function bubbleSort(numArr) {
  for (let i = 0; i &lt; numArr.length; i++) {
    for (let j = 0; j &lt; numArr.length - 1 - i; j++) {
      // console.log(numArr[j], numArr[j + 1]);
      if (numArr[j] &gt; numArr[j + 1]) {
        // 자리 바꿔줘야 함
        // swap 로직
        const temp = numArr[j];
        numArr[j] = numArr[j + 1];
        numArr[j + 1] = temp;
      }
    }
  }
  return numArr;
}
console.log(bubbleSort([5, 4, 8, 10, 2]));
// console.log(bubbleSort([5, 3, 8, 1, 2])); // [1, 2, 3, 5, 8]</code></pre>
<h3 id="주요-알고리즘-분류">주요 알고리즘 분류</h3>
<ul>
<li><strong>정렬:</strong> 퀵 정렬, 병합 정렬, 버블 정렬, 삽입 정렬, 선택 정렬</li>
<li><strong>탐색:</strong> 이진 탐색, 깊이 우선 탐색(DFS), 너비 우선 탐색(BFS)</li>
<li><strong>그래프:</strong> 다익스트라, 플로이드-워셜, 크루스칼, 프림</li>
<li><strong>동적 프로그래밍:</strong> 피보나치 수열, 배낭 문제, 최장 공통 부분 수열(LCS)</li>
<li><strong>문자열:</strong> KMP, 라빈-카프</li>
<li><strong>기타:</strong> 유클리드 호제법(GCD), 에라토스테네스의 체(소수 찾기)</li>
</ul>
<h2 id="💬-마치며"><strong>💬 마치며</strong></h2>
<p>오늘은 연습문제 위주로 풀고 마지막에 호이스팅과 컨텍스트에 대해 배웠다. 이전에 자바스크립트를 배웠을 때는 단순히 &quot;끌어올리는 것&quot; 정도로만 이해하고 있었는데 전체적인 동작 원리를 알게 되었다</p>
<p>호이스팅은 단순히 끌어올리는 것이 아니라, 자바스크립트의 동작 특성상 함수와 변수가 메모리에 먼저 저장되는 과정이라는 것을 이해할 수 있었다.</p>
<p>그리고 var로 선언된 변수는 호이스팅 시 초기값이 undefined가 되고, let과 const로 선언된 변수는 단순히 선언만 된 상태로 초기화 전까지는 접근할 수 없도록 동작한다는 것도 알게 됐다.</p>
<p>예전에는 &quot;var와 let, const의 차이가 뭐예요?&quot;라는 질문에 단순히 &quot;호이스팅&quot;이라고만 대답할 수 있었는데, 이제는 그 빈 공간을 채울 수 있는 지식을 얻은 것 같다 👍</p>
<p>그리고 최대공약수를 유클리드 호제법으로 직접 풀지는 못했지만, 강사님의 풀이를 통해 이해할 수 있었다. 최대공약수를 이용해 최소공배수를 구하는 방법도 배웠고, &quot;최대공약수 × 최소공배수 = a × b&quot;라는 공식도 알게 되었다. 문제 풀 때 써먹어 보고 싶다 나오려나? 🤔</p>
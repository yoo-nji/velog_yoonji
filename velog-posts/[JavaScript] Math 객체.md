<h2 id="math-객체-개요">Math 객체 개요</h2>
<p>JavaScript의 <code>Math</code> 객체는 수학 계산을 위한 내장 객체로, 다양한 상수와 메서드 제공. <strong>정적(static) 객체</strong>로, 인스턴스 생성 없이 바로 사용 가능. <code>Math.PI</code>나 <code>Math.abs()</code>와 같이 모든 속성과 메서드는 정적으로 <strong>직접 호출</strong>됨.</p>
<h3 id="주요-특성">주요 특성</h3>
<ul>
<li><strong>내장 객체</strong>: <code>Math</code>는 자바스크립트 엔진에 기본적으로 포함되어 있어 별도의 정의 없이 바로 사용 가능</li>
<li><strong>정적 메서드와 속성</strong>: <code>Math</code> 객체의 모든 메서드와 속성은 객체명과 함께 호출. 예: <code>Math.PI</code>나 <code>Math.sqrt()</code>와 같은 방식으로 호출<ul>
<li><strong>읽기 전용 속성</strong>: <code>Math</code> 객체의 상수들은 읽기 전용(read-only)으로 설정되어 수정 불가</li>
</ul>
</li>
</ul>
<p><strong>읽기 전용 속성의 이유</strong></p>
<ul>
<li><strong>정확성과 일관성 유지</strong>: 수학적 상수(예: <code>Math.PI</code>, <code>Math.E</code>)는 정확한 값을 유지해야 하므로 변경되지 않도록 설정됨</li>
<li><strong>오류 방지</strong>: 실수로 중요한 상수 값이 변경되는 것을 방지</li>
<li><strong>엔진 최적화</strong>: 자바스크립트 엔진이 최적화할 때, 고정된 값을 가진 상수가 있는 경우 성능 향상 가능</li>
</ul>
<p>예시: <code>Math.PI</code>는 변경 불가능. 값을 변경하려고 시도해도 원래의 값을 그대로 유지함:</p>
<pre><code class="language-jsx">Math.PI = 3.14; // 변경 시도
console.log(Math.PI); // 3.141592653589793 (변경되지 않음)</code></pre>
<hr />
<p>사용빈도 높음 ⭐️</p>
<p>알고리즘  💻</p>
<hr />
<h2 id="주요-속성">주요 속성</h2>
<h3 id="mathpi-⭐️"><strong>Math.PI ⭐️</strong></h3>
<p>설명: 원주율 π의 값을 반환합니다. </p>
<pre><code class="language-jsx">console.log(Math.PI); // 3.141592653589793</code></pre>
<h2 id="주요-메서드">주요 메서드</h2>
<h3 id="1-mathabsx-💻-⭐️">1. Math.abs(x) 💻 ⭐️</h3>
<p>주어진 수의 절댓값 반환</p>
<p>절대값: 어떤 수의 크기를 나타내는 양수 값. 음수의 경우 부호 제거한 값. 예: -5의 절대값은 5</p>
<pre><code class="language-jsx">console.log(Math.abs(-5)); // 5</code></pre>
<h3 id="2-mathceilx-⭐️">2. Math.ceil(x) ⭐️</h3>
<p>주어진 수보다 크거나 같은 정수 중 가장 작은 값 반환 (올림)</p>
<pre><code class="language-jsx">console.log(Math.ceil(4.2)); // 5</code></pre>
<h3 id="3-mathfloorx-⭐️">3. Math.floor(x) ⭐️</h3>
<p>주어진 수보다 작거나 같은 정수 중 가장 큰 값 반환 (내림)</p>
<pre><code class="language-jsx">console.log(Math.floor(4.8)); // 4</code></pre>
<h3 id="4-mathroundx-⭐️">4. Math.round(x) ⭐️</h3>
<p>주어진 수를 <code>반올림</code>하여 가장 가까운 정수 반환</p>
<pre><code class="language-jsx">console.log(Math.round(4.5)); // 5</code></pre>
<h3 id="5-mathrandomx-⭐️">5. Math.random(x) ⭐️</h3>
<p>0 이상 1 미만의 난수(무작위 실수) 반환</p>
<pre><code class="language-jsx">console.log(Math.random()); // 예: 0.123456789</code></pre>
<p><code>응용</code> 랜덤의 수를 뽑을 때 사용</p>
<pre><code class="language-jsx">// 1부터 6까지의 랜덤한 주사위 눈금 뽑기
function rollDice() {
    return Math.floor(Math.random() * 6) + 1;
}

console.log(rollDice()); // 1에서 6 사이의 랜덤한 정수 출력</code></pre>
<h3 id="6-mathpowbase-exponent-💻">6. Math.pow(base, exponent) 💻</h3>
<p>주어진 숫자의 거듭제곱 반환</p>
<pre><code class="language-jsx">console.log(Math.pow(2, 3)); // 8</code></pre>
<p><strong>응용: 원의 면적 계산</strong></p>
<pre><code class="language-jsx">function getCircleArea(radius) {
  return Math.PI * Math.pow(radius, 2);
}

console.log(getCircleArea(5)); // 78.53981633974483</code></pre>
<h3 id="7-mathmaxvalues-💻">7. Math.max(...values) 💻</h3>
<p>주어진 인수 중에서 가장 큰 값 반환</p>
<pre><code class="language-jsx">console.log(Math.max(1, 3, 2)); // 3</code></pre>
<h3 id="8-mathminvalues-💻">8. Math.min(...values) 💻</h3>
<p>주어진 인수 중에서 가장 작은 값 반환</p>
<pre><code class="language-jsx">console.log(Math.min(1, 3, 2)); // 1</code></pre>
<h3 id="9-mathsqrtx-💻">9. Math.sqrt(x) 💻</h3>
<p>주어진 수의 제곱근 반환</p>
<pre><code class="language-jsx">console.log(Math.sqrt(16)); // 4
console.log(Math.sqrt(10)); // 3.1622776601683795</code></pre>
<h3 id="10-mathsinx-mathcosx-mathtanx-💻">10. Math.sin(x), Math.cos(x), Math.tan(x) 💻</h3>
<p>각도를 라디안으로 받아 삼각 함수 반환</p>
<pre><code class="language-jsx">console.log(Math.sin(Math.PI / 2)); // 1
console.log(Math.cos(0)); // 1
console.log(Math.tan(Math.PI / 4)); // 1</code></pre>
<p><strong>피타고라스 정의 예제</strong></p>
<ul>
<li>직각삼각형에서 빗변의 제곱이 다른 두 변의 제곱의 합과 같음</li>
<li>수학식: a² + b² = c² (c는 빗변 길이)</li>
</ul>
<pre><code class="language-jsx">// 피타고라스 정리를 사용한 빗변 길이 계산
function calculateHypotenuse(a, b) {
  return Math.sqrt(Math.pow(a, 2) + Math.pow(b, 2));
}

console.log(calculateHypotenuse(3, 4)); // 출력: 5
console.log(calculateHypotenuse(5, 12)); // 출력: 13</code></pre>
<p>이 코드는 피타고라스 정리를 사용하여 직각삼각형의 빗변 길이를 계산. <code>Math.pow()</code>로 제곱을 계산하고, <code>Math.sqrt()</code>로 제곱근을 구함</p>
<h2 id="주의사항-및-팁-📌">주의사항 및 팁 📌</h2>
<ul>
<li><code>Math.random()</code>은 매 호출마다 다른 값을 반환하지만, 완전한 무작위성을 보장하지 않으므로 보안 목적에는 적합하지 않음</li>
<li>모든 <code>Math</code> 메서드는 입력값이 숫자가 아닐 경우 <code>NaN</code>을 반환할 수 있으니 입력값을 미리 확인하는 것이 좋음</li>
</ul>
<blockquote>
<p>📚 자세한 건 <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math">MDN 공식 문서</a> 참고</p>
</blockquote>
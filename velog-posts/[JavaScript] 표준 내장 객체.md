<h2 id="표준-내장-객체란">표준 내장 객체란?</h2>
<p><strong>표준 내장 객체</strong>는 자바스크립트 엔진에 내장된 객체로, 언제든지 사용할 수 있는 기본적인 기능 모음. 이 객체들은 복잡한 연산이나 반복되는 작업을 단순화해주며, 대부분의 자바스크립트 프로젝트에서 자주 사용됨</p>
<p><strong>예시:</strong></p>
<ul>
<li>배열을 쉽게 다루는 Array 객체</li>
<li>문자열 처리를 위한 String 객체</li>
<li>수학 연산에 유용한 Math 객체</li>
</ul>
<h2 id="표준-내장-객체의-특징">표준 내장 객체의 특징</h2>
<ul>
<li><strong>항상 사용 가능</strong>: 자바스크립트가 실행되는 모든 환경에서 기본으로 제공</li>
<li><strong>다양한 메서드 지원</strong>: 데이터 처리 및 조작을 위한 메서드들이 포함</li>
<li><strong>파괴적/비파괴적 메서드</strong>: 메서드가 데이터를 수정하는지 여부에 따라 구분</li>
</ul>
<blockquote>
<p><strong>파괴적 메서드</strong>: 원본 데이터를 수정하는 메서드. 예를 들어 Array.prototype.push()는 배열에 요소를 추가하면서 원본 배열을 수정</p>
</blockquote>
<blockquote>
<p><strong>비파괴적 메서드</strong>: 원본 데이터를 수정하지 않는 메서드. 예를 들어 Array.prototype.slice()는 배열의 일부를 반환하지만, 원본 배열은 변경되지 않음</p>
</blockquote>
<h2 id="브라우저-호환성-확인하기">브라우저 호환성 확인하기</h2>
<p><strong>표준 내장 객체</strong>와 그 메서드가 브라우저에서 지원되는지 확인하려면, <a href="https://caniuse.com/">Can I Use</a> 사이트를 활용 가능. 이 사이트는 다양한 브라우저에서 특정 자바스크립트 기능이나 메서드의 호환성을 보여줌</p>
<h2 id="자바스크립트-표준-내장-객체의-종류">자바스크립트 표준 내장 객체의 종류</h2>
<p>자바스크립트에서 자주 사용하는 대표적인 표준 내장 객체는 아래와 같음. 모든 객체와 메서드를 외우기보다는 필요할 때마다 문서를 참고하여 사용하는 것이 좋음</p>
<ol>
<li><strong>Object</strong>: 객체를 생성하고 조작할 수 있는 기본 객체</li>
<li><strong>Function</strong>: 함수에 대한 생성자와 메서드 제공</li>
<li><strong>Array</strong>: 배열을 다루기 위한 메서드와 속성 제공</li>
<li><strong>String</strong>: 문자열 조작을 위한 메서드 제공</li>
<li><strong>Boolean</strong>: 논리 값을 다루는 객체</li>
<li><strong>Number</strong>: 숫자를 처리하기 위한 객체</li>
<li><strong>Math</strong>: 수학 연산에 필요한 상수와 함수 제공</li>
<li><strong>Date</strong>: 날짜와 시간을 다루는 객체</li>
<li><strong>RegExp</strong>: 정규 표현식을 다루기 위한 객체</li>
</ol>
<h2 id="표준-내장-객체의-메서드---number-객체">표준 내장 객체의 메서드 - Number 객체</h2>
<p>JavaScript에서 <strong>Number 객체</strong>는 숫자를 처리할 때 유용한 여러 메서드를 제공. 아래는 자주 사용하는 몇 가지 예시</p>
<ul>
<li><p><strong>정적 메서드 (Static Method)</strong>: 인스턴스 생성 없이 객체 자체에서 호출할 수 있는 메서드</p>
<ul>
<li><p><code>Number.parseFloat()</code> - 문자열을 소수점 숫자로 변환</p>
<pre><code class="language-jsx">  console.log(Number.parseFloat('3.14')); // 출력: 3.14</code></pre>
</li>
<li><p><code>Number.parseInt()</code> - 문자열을 정수로 변환</p>
<pre><code class="language-jsx">  console.log(Number.parseInt('42')); // 출력: 42</code></pre>
</li>
<li><p><code>Number.isNaN()</code> - 값이 <code>NaN</code>인지 여부를 확인</p>
<pre><code class="language-jsx">  console.log(Number.isNaN(NaN)); // 출력: true</code></pre>
</li>
<li><p><code>Number.isFinite()</code> - 값이 유한한지 여부를 확인</p>
<pre><code class="language-jsx">  console.log(Number.isFinite(1)); // 출력: true</code></pre>
</li>
</ul>
</li>
<li><p><strong>인스턴스 메서드 (Instance Method)</strong>: 특정 숫자 인스턴스에서 호출할 수 있는 메서드</p>
<ul>
<li><p><code>toLocaleString()</code> - 숫자를 로케일 형식으로 변환하여 반환</p>
<pre><code class="language-jsx">  const num = 1000000;
  console.log(num.toLocaleString('ko-KR')); // 출력: 1,000,000</code></pre>
</li>
<li><p><code>valueOf()</code> - Number 객체의 원시 값을 반환</p>
<pre><code class="language-jsx">  const numObj = new Number(42);
  console.log(numObj.valueOf()); // 출력: 42</code></pre>
</li>
</ul>
</li>
</ul>
<h2 id="개발자-성향에-따른-사용법">개발자 성향에 따른 사용법</h2>
<p>개발자는 필요에 따라 <strong>표준 내장 객체</strong> 외에 라이브러리나 유틸리티를 추가로 사용 가능</p>
<ol>
<li><strong>표준 내장 객체</strong>: 기본적으로 자바스크립트 엔진에 내장된 기능 모음</li>
<li><strong>Lodash 같은 라이브러리</strong>: 표준 내장 객체에서 제공하지 않는 다양한 유틸리티 함수들을 제공</li>
</ol>
<blockquote>
<p>📚 자바스크립트의 표준 내장 객체에 대해 더 알고 싶다면, <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects">MDN 공식 문서</a>를 참고</p>
</blockquote>
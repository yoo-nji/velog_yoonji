<h2 id="1-enum의-기본-개념">1. enum의 기본 개념</h2>
<p><strong><code>enum</code>이란?</strong> <strong>고정된 값들의 집합</strong>을 정의할 때 사용되는 타입</p>
<p>ex) 성별(Gender)처럼 제한된 선택지가 있는 경우 유용</p>
<p><strong>사용목적</strong></p>
<ul>
<li>코드 가독성 향상 및 오류 방지</li>
<li>값의 '<code>열거</code>'에 중점</li>
</ul>
<p><strong>특징</strong></p>
<ul>
<li>타입스크립트에서만 제공되는 타입으로, <strong>숫자</strong> 또는 <strong>문자열</strong> 값들을 열거</li>
<li>코드에서 실수를 줄이고, 가독성을 높임</li>
</ul>
<hr />
<h2 id="2-숫자-열거형">2. 숫자 열거형</h2>
<p>특징: 각 항목에 <strong>숫자 값</strong>을 자동으로 할당</p>
<p>초기값이 없을 경우, 0부터 시작해 1씩 증가</p>
<pre><code class="language-tsx">enum Direction {
  UP, // 0
  DOWN, // 1
  LEFT, // 2
  RIGHT, // 3
}

console.log(Direction.UP); // 0
console.log(Direction.DOWN); // 1
console.log(Direction.LEFT); // 2
console.log(Direction.RIGHT); // 3</code></pre>
<blockquote>
<p>💡 실행 결과:<code>0, 1, 2, 3</code> 출력. 숫자가 자동으로 할당되어 초기값 지정 불필요</p>
</blockquote>
<h3 id="숫자형-enum의-초기값-지정">숫자형 <code>enum</code>의 초기값 지정</h3>
<p>숫자형 <code>enum</code>에서 특정 항목에 초기값을 지정하면, 이후 항목의 값도 자동으로 1씩 증가</p>
<pre><code class="language-tsx">enum Direction {
  UP,
  DOWN = 20,
  LEFT, // 21
  RIGHT, // 22
}

console.log(Direction.DOWN); // 20
console.log(Direction.LEFT); // 21
console.log(Direction.RIGHT); // 22</code></pre>
<blockquote>
<p>💡 실행 결과:<code>DOWN</code>은 20, 이후 값은 1씩 증가한 21, 22 출력</p>
</blockquote>
<hr />
<h2 id="3-문자열-열거형">3. 문자열 열거형</h2>
<p>문자열형 <code>enum</code>은 각 항목에 <strong>직접적인 문자열 값</strong>을 할당</p>
<p>⇒ 값의 의미를 더 직관적으로 표현 가능</p>
<pre><code class="language-tsx">enum Direction {
  UP = &quot;UP&quot;,
  DOWN = &quot;DOWN&quot;,
  LEFT = &quot;LEFT&quot;,
  RIGHT = &quot;RIGHT&quot;,
}

console.log(Direction.UP); // &quot;UP&quot;
console.log(Direction.DOWN); // &quot;DOWN&quot;
console.log(Direction.LEFT); // &quot;LEFT&quot;
console.log(Direction.RIGHT); // &quot;RIGHT&quot;</code></pre>
<blockquote>
<p>💡 실행 결과:<code>&quot;UP&quot;, &quot;DOWN&quot;, &quot;LEFT&quot;, &quot;RIGHT&quot;</code> 출력. 문자열 값은 의미가 명확하고 출력이 직관적이어서 선호되는 경우가 많음</p>
</blockquote>
<hr />
<h2 id="4-enum-사용-이유">4. <code>enum</code> 사용 이유</h2>
<p><code>enum</code>은 개발자가 제한된 선택지를 제공하여 <strong>실수 방지</strong>와 <strong>코드 안정성</strong> 향상에 유용함</p>
<h3 id="실수-가능성이-있는-코드-예시">실수 가능성이 있는 코드 예시</h3>
<p>아래 코드는 문자열을 직접 전달하여 오타나 잘못된 값으로 인한 오류 발생 가능성 존재</p>
<pre><code class="language-tsx">function move(direction: string) {
  switch (direction) {
    case &quot;UP&quot;:
      console.log(&quot;위로 한 칸 이동&quot;);
      break;
    case &quot;DOWN&quot;:
      console.log(&quot;아래로 한 칸 이동&quot;);
      break;
    case &quot;LEFT&quot;:
      console.log(&quot;왼쪽으로 한 칸 이동&quot;);
      break;
    case &quot;RIGHT&quot;:
      console.log(&quot;오른쪽으로 한 칸 이동&quot;);
      break;
    default:
      console.log(&quot;해당 값이 없음&quot;);
  }
}

move(&quot;up&quot;); // 실수로 소문자 사용 시 동작하지 않음</code></pre>
<h3 id="enum-사용한-개선된-코드"><code>enum</code> 사용한 개선된 코드</h3>
<p><code>enum</code> 사용 시 미리 정의된 값만 사용 가능하여 실수 감소</p>
<pre><code class="language-tsx">enum Direction {
  UP,
  DOWN,
  LEFT,
  RIGHT,
}

function move2(direction: Direction) {
  switch (direction) {
    case Direction.UP:
      console.log(&quot;위로 한 칸 이동&quot;);
      break;
    case Direction.DOWN:
      console.log(&quot;아래로 한 칸 이동&quot;);
      break;
    case Direction.LEFT:
      console.log(&quot;왼쪽으로 한 칸 이동&quot;);
      break;
    case Direction.RIGHT:
      console.log(&quot;오른쪽으로 한 칸 이동&quot;);
      break;
  }
}

move2(Direction.UP); // 위로 한 칸 이동</code></pre>
<blockquote>
<p>💡 실행 결과: &quot;위로 한 칸 이동&quot; 출력. 사용자가 제공하는 값이 열거형에 의해 제한되어 실수 방지 가능</p>
</blockquote>
<hr />
<h2 id="4-선언-병합-declaration-merging">4. 선언 병합 (Declaration Merging)</h2>
<p>문자열형 <code>enum</code>은 <strong>값이 중복되지 않는 경우</strong> 여러 선언 병합 가능</p>
<pre><code class="language-tsx">enum Gender {
  Male = &quot;Male&quot;,
}
enum Gender {
  Female = &quot;Female&quot;,
}

console.log(Gender.Male); // &quot;Male&quot;
console.log(Gender.Female); // &quot;Female&quot;</code></pre>
<blockquote>
<p>💡 실행 결과: &quot;Male&quot;, &quot;Female&quot; 출력</p>
</blockquote>
<h3 id="41-숫자형-enum의-병합-불가">4.1 숫자형 <code>enum</code>의 병합 불가</h3>
<p>숫자형 <code>enum</code>은 값이 자동으로 0부터 시작하여 <strong>중복된 값이 발생하여 병합 불가</strong></p>
<hr />
<h2 id="5-활용-예제">5. 활용 예제</h2>
<p><code>enum</code>은 특정 값 집합을 반복적으로 사용하는 경우 유용. 아래는 성별(Gender)을 나타내는 예제</p>
<pre><code class="language-tsx">enum Gender {
  Male = &quot;Male&quot;,
  Female = &quot;Female&quot;,
}

type User = {
  name: string;
  gender: Gender;
};

const user: User = {
  name: &quot;Alice&quot;,
  gender: Gender.Male, // 미리 정의된 값만 사용 가능
};

console.log(user.gender); // &quot;Male&quot;</code></pre>
<blockquote>
<p>💡 실행 결과: &quot;Male&quot; 출력. 성별 값이 제한되어 잘못된 값 사용 실수 방지 가능</p>
</blockquote>
<hr />
<h2 id="6-enum-vs-리터럴-타입">6. enum vs 리터럴 타입</h2>
<p>강사님의 선호: enum보다 리터럴 타입</p>
<ul>
<li>단, 같은 값이 여러 번 다른 타입으로 지정되어야 하는 경우에는 enum이 더 유용할 수 있음</li>
<li>enum 대신 리터럴 타입을 사용한 예시:</li>
</ul>
<pre><code class="language-tsx">type User = {
  name: string;
  gender: &quot;male&quot; | &quot;female&quot;;
};

// 객체 정의 시 실수 방지
const user: User = {
  name: &quot;Alice&quot;,
  gender: &quot;male&quot;,
};</code></pre>
<hr />
<h2 id="7-enum의-특징">7. enum의 특징</h2>
<pre><code class="language-tsx">enum Test {
  hi,
}
 //키값 추적하기
console.log(Test[0]); // &quot;hi&quot;</code></pre>
<hr />
<h2 id="8-const-enum">8. const enum</h2>
<p><a href="https://www.typescriptlang.org/play/#code/PTAEHUFMBsGMHsC2lQBd5oBYoCoE8AHSAZVgCcBLA1UABWgEM8BzM+AVwDsATAGiwoBnUENANQAd0gAjQRVSQAUCEmYKsTKGYUAbpGF4OY0BoadYKdJMoL+gzAzIoz3UNEiPOofEVKVqAHSKymAAmkYI7NCuqGqcANag8ABmIjQUXrFOKBJMggBcISGgoAC0oACCbvCwDKgU8JkY7p7ehCTkVDQS2E6gnPCxGcwmZqDSTgzxxWWVoASMFmgYkAAeRJTInN3ymj4d-jSCeNsMq-wuoPaOltigAKoASgAywhK7SbGQZIIz5VWCFzSeCrZagNYbChbHaxUDcCjJZLfSDbExIAgUdxkUBIursJzCFJtXydajBBCcQQ0MwAUVWDEQC0gADVHBQGNJ3KAALygABEAAkYNAMOB4GRonzFBTBPB3AERcwABS0+mM9ysygc9wASmCKhwzQ8ZC8iHFzmB7BoXzcZmY7AYzEg-Fg0HUiQ58D0Ii8fLpDKZgj5SWxfPADlQAHJhAA5SASPlBFQAeS+ZHegmdWkgR1QjgUrmkeFATjNOmGWH0KAQiGhwkuNok4uiIgMHGxCyYrA4PCCJSAA">TypeScript 플레이그라운드</a>: 브라우저에서 TypeScript 코드 작성 및 실행 가능한 온라인 도구. 설치 없이 코드 작성 및 JavaScript 변환 실시간 확인 가능</p>
<h3 id="enum-단점">enum 단점</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/4cc1c54c-82f7-4ea4-8954-e054424652d8/image.png" /></p>
<p>컴파일 시 사진처럼 코드가 길어짐</p>
<p>무분별한 enum 사용은 컴파일된 코드의 길이를 증가시킴</p>
<p>✅ <strong>코드 흔적을 남기지 않는 방법</strong></p>
<p>enum 앞에 const를 붙임</p>
<p>실무에서는 주로 이런 const enum을 사용함</p>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/12876370-1962-48ad-9652-828ad0b567cc/image.png" /></p>
<h2 id="const-여부에-따른-컴파일-결과물-차이">const 여부에 따른 컴파일 결과물 차이</h2>
<ul>
<li><strong>일반 enum:</strong> 컴파일 시 JavaScript 객체로 변환되어 런타임에도 존재함</li>
<li><strong>const enum:</strong> 컴파일 시 해당 값으로 인라인 대체되어 런타임에 객체가 생성되지 않음</li>
</ul>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>
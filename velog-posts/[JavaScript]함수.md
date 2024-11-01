<p><strong>함수 사용 이유</strong></p>
<ul>
<li>높은 재활용성</li>
<li>애플리케이션 전역에서 호출 가능</li>
<li>코드 중복 감소</li>
<li>유지보수 용이성 향상</li>
</ul>
<h2 id="함수-선언문">함수 선언문</h2>
<h3 id="함수-선언식-기본">함수 선언식 (기본)</h3>
<pre><code class="language-jsx">function func(){
  //code
}</code></pre>
<p><strong>호출</strong></p>
<pre><code class="language-jsx">function sum(){}; 
sum(); // 호출</code></pre>
<p>예시: 구구단 코드 실행</p>
<pre><code class="language-jsx">// 함수 선언문
function gugudan() {
  for (let i = 1; i &lt;= 9; i++) {
    console.log(`${i}단`);
    for (let j = 1; j &lt;= 9; j++) {
      console.log(`${i} * ${j} = ${i * j}`);
    }
    console.log(&quot;-&quot;);
  }
}

gugudan(); // 함수 호출</code></pre>
<h2 id="함수-표현식">함수 표현식</h2>
<p>표현식: 값으로 평가 가능한 식</p>
<h3 id="네이밍-함수">네이밍 함수</h3>
<p>네이밍 함수: 변수에 함수 할당하여 생성함</p>
<pre><code class="language-jsx">const func = function(){}; //unnamed function 
let func2 = function sum(){}; //named function</code></pre>
<p><strong>함수 선언 시 변수로 let과 const 중 어떤 것을 사용할지에 대한 고려사항</strong></p>
<ul>
<li><code>const</code> 사용이 일반적</li>
<li>이유: 함수의 재할당 방지 및 코드 안정성 향상</li>
<li>let 사용 상황: 특별히 함수 재할당이 필요한 경우</li>
<li>권장 사항: const를 기본으로 사용하고, 필요 시에만 let 고려</li>
<li>함수 재할당은 거의 발생하지 않음</li>
</ul>
<h3 id="익명-함수화살표함수">익명 함수(화살표함수)</h3>
<p><strong>함수 선언문과 화살표 함수 비교</strong></p>
<ul>
<li>화살표 함수는 'function' 키워드 대신 '=&gt;' 화살표 사용</li>
<li>화살표 위치: 매개변수를 감싸는 소괄호와 함수 본문을 감싸는 중괄호 사이</li>
<li>변수명 지정 필요 (호출용)</li>
</ul>
<pre><code class="language-jsx">// 함수 선언문
function gugudan() {};

// 화살표 함수
const gugudan = () =&gt; {};</code></pre>
<p><strong>호출</strong></p>
<p><code>변수명</code>으로 호출</p>
<pre><code class="language-jsx">변수명()</code></pre>
<h2 id="함수의-매개변수">함수의 매개변수</h2>
<p>함수를 호출할 때 사용자가 <strong>원하는 값을 함수로 전달</strong>할 수 있게 해 주는 것</p>
<pre><code class="language-jsx">function gugudan(dan)//매개변수
{
  for (let j = 1; j &lt;= 9; j++) {
    console.log(`${dan} * ${j} = ${dan * j}`);
  }
}

gugudan(1);//인자(인수)</code></pre>
<h3 id="매개변수와-인자의-차이점">매개변수와 인자의 차이점</h3>
<p>매개변수(parameter)와 인자(argument)는 서로 다른 개념이지만, 일상 대화에서는 '매개변수'로 통칭되기도 함</p>
<ul>
<li><strong>매개변수:</strong> 함수 정의 시 사용되는 변수</li>
<li><strong>인자:</strong> 함수 호출 시 전달되는 실제 값</li>
</ul>
<p>두 용어는 종종 혼용되며, 맥락에 따라 의미 전달이 가능함</p>
<h3 id="매개변수와-인자의--유연성">매개변수와 인자의  유연성</h3>
<p>매개변수와 인자의 수는 일반적으로 일치해야 함. 그러나 JavaScript의 유연성으로 인해 다음과 같은 상황 발생 가능:</p>
<ul>
<li>매개변수보다 적은 인자 전달: 나머지 매개변수는 undefined로 설정됨</li>
<li>매개변수보다 많은 인자 전달: 추가 인자는 무시됨</li>
<li>가변 인자 함수: rest 파라미터(...args)를 사용하여 여러 인자를 배열로 받을 수 있음</li>
</ul>
<h3 id="매개변수-사용-예시">매개변수 사용 예시</h3>
<p>함수 선언식, 표현식, 화살표 함수에서 매개변수 사용:</p>
<pre><code class="language-jsx">// 선언식
function greet(name) {
  console.log(`Hi, ${name}!`);
}

// 표현식
const greet = function(name) {
  console.log(`Hi, ${name}!`);
};

// 화살표 함수
const greet = name =&gt; console.log(`Hi, ${name}!`);</code></pre>
<p>화살표 함수: 매개변수가 하나면 괄호 생략 가능, 없거나 둘 이상이면 필요.</p>
<h3 id="기본-매개변수">기본 매개변수</h3>
<p>함수 정의 시 매개변수에 <code>기본값</code> 설정 가능. 인자 생략 시 기본값 적용.</p>
<pre><code class="language-jsx">function gugudan(dan, start, end = 20) {
  for (let i = start; i &lt;= end; i++) {
    console.log(`${dan} * ${i} = ${dan * i}`);
  }
}

gugudan(3, 2, 4);</code></pre>
<p>'end' 기본값은 20. 다른 값 전달 시 대체됨.</p>
<h3 id="가변인자-처리">가변인자 처리</h3>
<ol>
<li><p><strong>나머지 매개변수(ES6) <code>실무</code></strong></p>
<p> (=스프레드 연산자/전개연산자)</p>
<p> 나머지 매개변수: 함수에 전달된 여러 인수를 배열로 받아 처리</p>
<p> 특징:</p>
<ul>
<li><p>...args 형태로 함수 정의</p>
</li>
<li><p>여러 인수를 단일 배열로 수집</p>
</li>
<li><p>배열 메서드 활용 가능</p>
</li>
<li><p>arguments보다 직관적이고 유연함</p>
<p>주의:</p>
</li>
<li><p>매개변수에서 마지막에 위치해야 함</p>
<pre><code class="language-jsx">function sum(...args){
console.log(args[0] + args[1]);
}
sum(10,20);</code></pre>
</li>
</ul>
</li>
</ol>
<ol>
<li><p><strong>Arguments</strong></p>
<ul>
<li><p>arguments: 함수에 전달된 인자들을 <strong>유사 배열 객체</strong>로 저장</p>
</li>
<li><p><strong>Arguments 객체를 사용한 함수의 기능</strong>:</p>
<ul>
<li>모든 전달된 인자를 순회하며 합산</li>
<li>합산된 결과를 반환</li>
</ul>
</li>
<li><p>예시: sum(10, 20, 30)은 <strong>60</strong>, sum(10, 20, 30, 40)은 <strong>100</strong> 반환</p>
<pre><code class="language-jsx">  function sum() {
      let sum = 0;  // 합계를 저장할 변수 초기화
      for (let value of arguments) {  // arguments 객체의 각 인자를 순회
          sum += value;  // 각 인자를 합산
      }
      return sum;  // 최종 합계 반환
  }

  console.log(sum(10, 20, 30));  // 출력: 60
  console.log(sum(10, 20, 30, 40));  // 출력: 100</code></pre>
</li>
</ul>
</li>
</ol>
<pre><code>**`주의`**

- arguments는 **화살표 함수에서 사용 불가**
- 실무에선 `나머지 매개변수` 사용 권장</code></pre><h2 id="반환return">반환(return)</h2>
<p><strong>함수에서 반환을 사용하는 주요 이유:</strong></p>
<ul>
<li>함수의 결과를 외부로 전달</li>
<li>함수 실행의 즉시 종료 및 값 반환</li>
<li>계산된 결과의 재사용 가능</li>
</ul>
<p><strong>JavaScript 함수의 반환 관련 특징:</strong></p>
<ul>
<li>명시적 return 없으면 암묵적으로 undefined 반환</li>
<li>return 문 이후의 코드는 실행되지 않음</li>
<li>함수는 단일 값만 반환 (다중 값 반환 시 배열이나 객체 사용)</li>
</ul>
<h3 id="1-기본-반환-사용법">1. 기본 반환 사용법</h3>
<p>함수에서 return 문을 사용하여 값을 반환하는 기본적인 방법:</p>
<p>아래 예시에서 sum 함수는 두 숫자의 합을 반환하며, 이 값은 변수에 저장되어 재사용됨. return 문은 함수의 실행을 즉시 종료하고 계산된 결과를 반환함</p>
<pre><code class="language-jsx">//반환
const sum = (n1, n2) =&gt; {
  const result = n1 + n2;
  return result; //함수 밖으로 원하는 값을 전달
};

const result = sum(10, 20); // 함수 밖에서도 선언을 해 줘야 사용 가능함
console.log(result);</code></pre>
<p><strong>같은 const로 같은 식별자를 사용할 수 있는 이유:</strong></p>
<p>함수 내부의 result와 외부의 result는 서로 다른 <a href="https://www.notion.so/129f16da468d80f48ddbf3c1e67f4ff6?pvs=21"><strong>스코프</strong></a>에 존재함. 두 변수는 이름만 같을 뿐, 실제로는 완전히 별개의 변수임. 따라서 같은 이름 사용 가능함</p>
<h3 id="2-화살표-함수의-간결한-문법"><strong>2. 화살표 함수의 간결한 문법</strong></h3>
<p>화살표 함수에서는 중괄호와 return 키워드를 생략 가능함. 이는 함수가 단일 표현식을 즉시 반환할 때 유용함</p>
<pre><code class="language-jsx">const sum = (n1, n2) =&gt; {
  const result = n1 + n2; // 불필요한 변수 선언
  return result; // 직접 반환하는 것이 더 효율적
};

const result = sum(10, 20);
console.log(result); // 30

// 더 효율적인 방법:
const sum = (n1, n2) =&gt; n1 + n2;

const result = sum(10, 20);
console.log(result); // 30</code></pre>
<pre><code class="language-jsx">const sum = (n1, n2) =&gt; n1 + n2;</code></pre>
<h3 id="3-객체-리터럴-반환-시-주의사항">3. 객체 리터럴 반환 시 주의사항</h3>
<p>객체를 반환할 때는 소괄호로 객체 리터럴을 감싸야 함. 그렇지 않으면 중괄호가 함수 본문으로 해석될 수 있음</p>
<pre><code class="language-jsx">// 잘못된 방식
const getUser = () =&gt; { name: &quot;철수&quot; }; // 오류 발생

// 올바른 방식
const getUser = () =&gt; ({ name: &quot;철수&quot; });</code></pre>
<p>이러한 문법적 특징들을 이해하면 더 간결하고 가독성 있는 코드를 작성 가능함</p>
<h3 id="return을-사용한-코드-실행-제어-효율적인-함수-종료-방법">return을 사용한 코드 실행 제어: 효율적인 함수 종료 방법</h3>
<p>return을 사용해 함수 실행을 제어하는 것이 중요함. return은 함수를 즉시 종료하고 값을 반환함</p>
<p><strong>return의 주요 기능:</strong></p>
<ul>
<li>함수 실행 중단 및 값 반환</li>
<li>이후 코드 실행 방지</li>
</ul>
<p><strong>조건부 함수 종료:</strong></p>
<ul>
<li>특정 조건에서 함수 조기 종료</li>
<li>불필요한 연산 방지로 효율성 증가</li>
</ul>
<pre><code class="language-jsx">function gugudan(dan) {
    if (dan === 3) {
        console.log(&quot;3단은 출력하지 않음&quot;);
        return;
    }
    for (let i = 1; i &lt;= 9; i++) {
        console.log(`${dan} * ${i} = ${dan * i}`);
    }
}

gugudan(3);  // 3단은 출력하지 않음</code></pre>
<p><strong>코드 실행 흐름:</strong></p>
<ul>
<li>gugudan(3) 호출 시: 조건이 참이면 메시지 출력 후 함수 종료</li>
<li>다른 단 입력 시: 조건이 거짓이면 구구단 출력</li>
</ul>
<h2 id="스코프">스코프</h2>
<p><strong><code>스코프</code></strong> 식별자를 참조할 수 있는 범위를 의미</p>
<ul>
<li>지역 스코프 → 전역 스코프 참조 <strong><code>가능</code></strong></li>
<li>전역 스코프 → 지역 스코프 참조 <strong><code>불가능</code></strong></li>
</ul>
<h3 id="1-전역-스코프">1. 전역 스코프</h3>
<ul>
<li>프로그램 전체에서 사용 가능</li>
<li>전역 변수는 어디서든 접근 및 수정 가능</li>
</ul>
<h3 id="2-지역-스코프">2. 지역 스코프</h3>
<ol>
<li><p><strong>함수 스코프</strong></p>
<ul>
<li><p>함수 내에서만 유효한 범위</p>
<pre><code class="language-jsx">// 전역 스코프
let a = &quot;전역 변수&quot;;

function exampleFunction() {
// 지역 스코프
let b = &quot;지역 변수&quot;;
console.log(a);  // 접근 가능
console.log(b);  // 접근 가능
}

exampleFunction();
console.log(a);  // 접근 가능
console.log(b);  // 오류: b is not defined</code></pre>
</li>
</ul>
</li>
<li><p><strong>블록 스코프</strong></p>
<pre><code class="language-jsx"> if (true) {
   let a = &quot;블록 변수&quot;;
   console.log(a);  // 접근 가능
 }
 console.log(a);  // 오류: a is not defined</code></pre>
<ul>
<li><p><strong>중첩된 블록 스코프</strong></p>
<pre><code class="language-jsx">if (true) {
let a = &quot;외부 블록 변수&quot;;
console.log(a);  // 접근 가능

if (true) {
  let b = &quot;내부 블록 변수&quot;;
  console.log(a);  // 외부 블록 변수에 접근 가능
  console.log(b);  // 내부 블록 변수에 접근 가능
}

console.log(b);  // 오류: b is not defined
}
console.log(a);  // 오류: a is not defined</code></pre>
</li>
<li><p>중첩된 블록에서는 내부 블록이 외부 블록의 변수에 접근할 수 있지만, 그 반대는 불가능. 이는 블록 스코프의 계층적 특성을 보여줌</p>
</li>
<li><p><strong><code>주의</code></strong> let과 const만 블록 스코프를 생성함</p>
</li>
</ul>
</li>
</ol>
<h3 id="전역스코프-지역스코프-비교">전역스코프 지역스코프 비교</h3>
<table>
<thead>
<tr>
<th><strong>특성</strong></th>
<th><strong>전역 스코프</strong></th>
<th><strong>지역 스코프</strong></th>
</tr>
</thead>
<tbody><tr>
<td>정의</td>
<td>코드의 어느 곳에서나 접근 가능한 변수의 범위</td>
<td>특정 함수 또는 블록 내에서만 접근 가능한 변수의 범위</td>
</tr>
<tr>
<td>접근성</td>
<td>프로그램의 모든 부분에서 접근 가능</td>
<td>정의된 함수 또는 블록 내에서만 접근 가능</td>
</tr>
<tr>
<td>생명 주기</td>
<td>프로그램이 종료될 때까지 유지</td>
<td>함수 실행이 끝나거나 블록을 벗어나면 소멸</td>
</tr>
<tr>
<td>메모리 사용</td>
<td>항상 메모리를 차지</td>
<td>필요할 때만 메모리를 사용하고 해제</td>
</tr>
<tr>
<td>이름 충돌</td>
<td>이름 충돌 가능성이 높음</td>
<td>같은 이름의 변수를 다른 함수에서 사용 가능, 충돌 위험 낮음</td>
</tr>
<tr>
<td>코드 관리</td>
<td>전역 변수가 많아지면 코드 관리가 어려워질 수 있음</td>
<td>변수의 영향 범위가 제한되어 코드 관리가 용이</td>
</tr>
</tbody></table>
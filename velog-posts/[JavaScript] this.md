<h2 id="this의-기본-개념">this의 기본 개념</h2>
<p><strong>this란?</strong> 현재 코드가 실행되는 시점에서 그 함수를 호출한 객체를 가리키는 키워드. &quot;호출한 주체&quot;에 따라 this의 값이 달라질 수 있음</p>
<h2 id="전역-스코프에서의-함수와-this">전역 스코프에서의 함수와 this</h2>
<p><strong>전역 스코프에서 선언된 함수는 <code>window</code> 객체의 메서드로 등록</strong></p>
<p>예시:</p>
<pre><code class="language-jsx">function sayHello() {
  console.log(this);
}

sayHello();        // window 출력
window.sayHello(); // window 출력

console.log(window);
// 출력: Window {sayHello: ƒ, ...}</code></pre>
<h2 id="객체-메서드와-this">객체 메서드와 this</h2>
<p>객체의 메서드 내에서 <code>this</code>를 사용하면 해당 객체의 속성에 접근 가능. 객체 내부에서 자신의 속성을 쉽게 참조할 수 있음</p>
<p>예시:</p>
<pre><code class="language-jsx">const person = {
  name: &quot;철수&quot;,
  age: 18,
  introduce: function() {
    console.log(`안녕하세요, 제 이름은 ${this.name}이고 ${this.age}살입니다.`);
  }
};

person.introduce(); // 출력: 안녕하세요, 제 이름은 철수이고 18살입니다.</code></pre>
<h3 id="this-사용의-이점">this 사용의 이점</h3>
<p><code>this</code> 키워드 사용 시 객체 내부에서 자신의 속성들을 쉽게 참조 가능. 코드의 재사용성과 유지보수성 향상.</p>
<p><strong>this를 사용하지 않은 예제</strong></p>
<pre><code class="language-jsx">const person = {
  name: &quot;철수&quot;,
  age: 18,
  introduce: function() {
    console.log(&quot;안녕하세요, 제 이름은 &quot; + person.name + &quot;이고 &quot; + person.age + &quot;살입니다.&quot;);
  }
};

person.introduce(); // 출력: 안녕하세요, 제 이름은 철수이고 18살입니다.</code></pre>
<p>this 미사용 시 객체 이름(예: person) 변경 때 메서드 내부의 모든 참조 수정 필요. this 사용 시 객체 이름 변경되어도 메서드 내부 코드 수정 불필요.</p>
<h2 id="화살표-함수에서의-this">화살표 함수에서의 this</h2>
<p>화살표 함수에서 <code>this</code>는 일반 함수와 다르게 동작:</p>
<ul>
<li>화살표 함수는 자신만의 <code>this</code>를 생성하지 않음</li>
<li>함수가 <strong>&quot;정의될 때&quot;의 스코프에 있는 <code>this</code></strong>를 사용</li>
<li>이를 '렉시컬 this' 또는 '어휘적 this'라고 함</li>
</ul>
<h3 id="1-일반-함수와-화살표-함수의-차이">1. 일반 함수와 화살표 함수의 차이</h3>
<pre><code class="language-jsx">const obj = {
  name: &quot;철수&quot;,
  regularFunc: function() {
    console.log(&quot;Regular function:&quot;, this.name);
  },
  arrowFunc: () =&gt; {
    console.log(&quot;Arrow function:&quot;, this.name);
  }
};

obj.regularFunc(); // 출력: Regular function: 철수
obj.arrowFunc();   // 출력: Arrow function: undefined</code></pre>
<p>이 예제에서 화살표 함수 내의 <code>this</code>는 전역 객체를 가리키므로, <code>this.name</code>은 <code>undefined</code>가 됨</p>
<h3 id="2-렉시컬-스코프의-동작">2. 렉시컬 스코프의 동작</h3>
<pre><code class="language-jsx">const obj = {
  name: &quot;윤지&quot;,
  regularFunc: function() {
    const arrowFunc = () =&gt; {
      console.log(this.name); // regularFunc의 `this` 사용
    };
    arrowFunc();
  }
};

obj.regularFunc(); // 출력: 윤지</code></pre>
<ul>
<li><code>arrowFunc</code>는 <code>regularFunc</code>의 스코프에서 정의되어 <code>obj</code>를 가리킴</li>
<li>화살표 함수는 자신의 <code>this</code>를 만들지 않고, 감싸는 함수의 <code>this</code>를 사용</li>
</ul>
<h3 id="3-화살표-함수의-설계-목적">3. 화살표 함수의 설계 목적</h3>
<p>화살표 함수는 <code>this</code>를 일관되게 유지하기 위해 설계:</p>
<ul>
<li>일반 함수에서는 호출 주체에 따라 <code>this</code>가 바뀌어 예기치 않은 버그가 발생할 수 있음</li>
<li>화살표 함수는 렉시컬 스코프를 따라 <code>this</code>가 바뀌지 않도록 설계됨</li>
</ul>
<h2 id="생성자-함수에서의-this"><strong>생성자 함수에서의 this</strong></h2>
<h3 id="1-생성자-함수의-개념">1. <strong>생성자 함수의 개념</strong></h3>
<ul>
<li>생성자 함수: <strong>새로운 객체를 만들기 위한 템플릿</strong></li>
<li><strong><code>new</code> 키워드</strong>로 호출 시 <strong>새로운 객체</strong> 생성, 그 객체 내에서 <code>this</code> 사용</li>
</ul>
<h3 id="2-예제-코드">2. <strong>예제 코드</strong></h3>
<pre><code class="language-jsx">function 고양이(고양이이름) {
  this.이름 = 고양이이름;  // 'this.이름'은 새로 생성된 고양이 객체의 속성
}

const 아기고양이 = new 고양이(&quot;네로&quot;);
console.log(아기고양이.이름); // 출력: '네로'</code></pre>
<ul>
<li><code>고양이이름</code>: 함수 호출 시 전달받는 매개변수</li>
<li><code>this.이름</code>: 새로 생성된 고양이 객체의 속성<ul>
<li><strong><code>this</code></strong>는 새로 생성된 고양이 객체를 가리킴</li>
<li>고양이 객체에 <strong><code>이름</code></strong> 속성 생성, <code>&quot;네로&quot;</code> 값 할당</li>
</ul>
</li>
</ul>
<h3 id="3-생성자-함수에서-this를-사용하지-않는-경우">3. 생성자 함수에서 <strong>this를 사용하지 않는 경우</strong></h3>
<pre><code class="language-jsx">function 고양이(고양이이름) {
  const 이름 = 고양이이름;  // 지역 변수에 이름 저장
}

const 아기고양이 = new 고양이(&quot;네로&quot;);
console.log(아기고양이.이름); // 출력: undefined</code></pre>
<ul>
<li>아기고양이 객체에 이름 속성이 생성되지 않음</li>
<li><code>이름</code>은 함수 내부의 지역 변수로만 존재</li>
<li>함수 실행 종료 시 지역 변수 소멸, 객체에 정보 저장되지 않음</li>
</ul>
<h3 id="4-정리">4. <strong>정리</strong></h3>
<ul>
<li><strong><code>this</code> 미사용</strong>: 값이 지역 변수에만 저장되어 함수 종료 시 소멸</li>
<li><strong><code>this</code> 사용</strong>: 생성된 객체의 속성으로 값 저장, 이후 객체를 통해 접근 가능</li>
</ul>
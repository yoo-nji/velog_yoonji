<h2 id="자바스크립트의-클래스-개념과-도입-이유">자바스크립트의 클래스 개념과 도입 이유</h2>
<p>자바스크립트는 객체지향 언어이나 <strong>전통적 객체지향과 차이</strong>가 존재함. Java 등의 <strong>클래스 기반 객체지향</strong>과 달리 <strong>프로토타입 기반 객체지향</strong> 사용.</p>
<p>⇒ 이를 보완하기 위해 ES6에서 <strong>클래스</strong> 문법 도입</p>
<hr />
<h2 id="객체지향-언어의-두-가지-유형">객체지향 언어의 두 가지 유형</h2>
<ol>
<li><strong>클래스 기반 객체지향</strong>: Java, C++ 등이 사용. 일반적인 객체지향 언어로 지칭</li>
<li><strong>프로토타입 기반 객체지향</strong>: 자바스크립트 방식. 객체가 프로토타입 체인으로 상속과 속성 공유 구현</li>
</ol>
<p><strong><code>자바스크립트 클래스란?</code></strong> 새로운 객체지향 개념이 아닌 <strong>프로토타입 기반 상속을 쉽게 사용할 수 있는 문법적 설탕</strong>. 기존 개념을 쉽게 활용하도록 도움</p>
<h2 id="클래스의-기본-구조">클래스의 기본 구조</h2>
<pre><code class="language-jsx">class ClassName {
  constructor() {
    // 생성자 메서드
  }

  method1() {
    // 메서드 1
  }

  method2() {
    // 메서드 2
  }
}</code></pre>
<h3 id="클래스-정의-요소"><strong>클래스 정의 요소</strong></h3>
<ul>
<li><strong>class 키워드</strong>: 클래스 정의</li>
<li><strong>ClassName</strong>: 클래스 이름. 일반적으로 대문자로 시작</li>
<li><strong>constructor</strong>: 생성자 메서드. 클래스 인스턴스 생성 시 <strong>한 번만 호출</strong>. <code>new</code> 키워드로 호출. 매개변수로 인스턴스 속성 초기화 가능</li>
<li><strong>method1, method2</strong>: 클래스의 메서드들</li>
</ul>
<h3 id="생성자-메서드constructor">생성자 메서드(constructor)</h3>
<p>생성자 메서드 <strong><code>constructor</code></strong>: 클래스의 인스턴스를 생성하고 초기화하는 특별한 메서드</p>
<ul>
<li>클래스 내 단 하나만 존재, 여러 개 정의 시 SyntaxError 발생</li>
<li>인스턴스 <strong>생성 시 자동으로 호출</strong></li>
<li>인스턴스의 초기 상태 설정에 사용, 필요한 매개변수 정의</li>
</ul>
<h3 id="클래스-사용-예시">클래스 사용 예시</h3>
<pre><code class="language-jsx">class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  getInfo() {
    return `${this.name}, ${this.age}`;
  }
}

const personC = new Person(&quot;철수&quot;, 30);
console.log(personC.getInfo()); // 출력: 철수, 30</code></pre>
<h2 id="생성자-함수와-클래스의-비교">생성자 함수와 클래스의 비교</h2>
<h3 id="1-생성자-함수-방식">1. 생성자 함수 방식</h3>
<pre><code class="language-jsx">function PersonF(name, age) {
  this.name = name;
  this.age = age;

  this.getInfo = function() {
    console.log(`${this.name}, ${this.age}`);
  };
}

const personF = new PersonF(&quot;철수&quot;, 20);</code></pre>
<ul>
<li><strong>특징</strong>: 생성자 함수로 객체 생성. 함수로 선언되어 각 인스턴스에 메서드 저장</li>
<li><strong>비효율성</strong>: 생성자 함수 방식에서 각 인스턴스마다 메서드 중복 저장. 메모리 사용 비효율적 가능성</li>
<li><strong>해결 방법</strong>: 프로토타입 사용해 메서드 추가 시 메모리 효율 개선 가능</li>
</ul>
<pre><code class="language-jsx">PersonF.prototype.getInfo = function() {
  console.log(`${this.name}, ${this.age}`);
};</code></pre>
<p><code>getInfo</code> 메서드: 프로토타입 객체에 저장. 모든 인스턴스가 이 메서드 공유. 메모리 사용량 감소</p>
<h3 id="2-클래스-방식">2. 클래스 방식</h3>
<pre><code class="language-jsx">class PersonC {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  getInfo() {
    return `${this.name}, ${this.age}`;
  }
}

const personC = new PersonC(&quot;영희&quot;, 30);</code></pre>
<ul>
<li><strong>특징</strong>: 클래스 메서드 자동으로 프로토타입에 저장. 메모리 사용량 감소, 재사용성 향상</li>
<li><strong>자동화</strong>: 메서드 <strong>프로토타입 추가 불필요</strong>. 클래스 내부에 메서드 직접 작성 가능</li>
<li><strong>설명</strong>: <code>constructor</code> 메서드 인스턴스 생성 시 자동 호출. 인스턴스의 초기 속성 설정 역할</li>
</ul>
<h3 id="두-방식의-차이점">두 방식의 차이점</h3>
<ol>
<li><strong>구문</strong>: 생성자 함수는 <code>function</code> 키워드를, 클래스는 <code>class</code> 키워드를 사용한다.</li>
<li><strong>생성자 메서드</strong>: 함수는 매개변수를 직접 정의하지만, 클래스는 <code>constructor</code> 메서드 내에서 정의한다.</li>
<li><strong>프로토타입 메서드 정의</strong>: 함수는 <code>prototype</code> 객체를 통해 메서드를 추가하지만, 클래스는 내부에 직접 메서드를 정의한다.</li>
<li><strong>편의성</strong>: 클래스는 더 직관적이고 명확한 객체지향 문법을 제공한다.</li>
<li><strong>유지보수</strong>: 클래스는 ES6 이후 표준화되어 코드의 가독성과 유지보수성이 향상되었다.</li>
</ol>
<h2 id="클래스-사용이-권장되는-이유">클래스 사용이 권장되는 이유</h2>
<p>클래스와 생성자 함수: 둘 다 자바스크립트의 객체지향 특성 반영. ES6 이후 <strong>클래스 사용 권장</strong></p>
<ul>
<li><strong>가독성</strong>: 클래스 구문이 더 직관적. 객체지향 구조 쉽게 구현 가능</li>
<li><strong>메모리 효율성</strong>: 메서드가 자동으로 프로토타입에 저장. 여러 인스턴스가 공용으로 사용</li>
</ul>
<h2 id="프로토타입-정의">프로토타입 정의</h2>
<p><strong><code>프로토타입</code>:</strong> 자바스크립트 함수의 특별 객체로, 생성자 함수로 만든 객체들이 공유하는 <strong>공통 공간</strong>. 함수와 1:1 매칭되며, 해당 생성자의 모든 인스턴스가 접근 가능</p>
<ul>
<li><strong>프로토타입의 역할</strong>: 프로토타입 객체에 <strong>공통적으로 사용될 속성이나 메서드를 정의</strong>하여, 메모리 낭비 감소</li>
<li><strong>프로토타입 객체가 필요한 이유</strong>: 생성자 함수로 인스턴스를 만들 때마다 같은 메서드를 계속 생성하면 메모리 낭비 발생. 반복적으로 사용할 메서드는 프로토타입에 정의하여 <strong>모든 인스턴스가 공유</strong>하는 것이 효율적</li>
</ul>
<hr />
<h2 id="프로토타입을-이용한-메모리-최적화">프로토타입을 이용한 메모리 최적화</h2>
<h3 id="메모리를-비효율적으로-사용하는-예"><strong>메모리를 비효율적으로 사용하는 예</strong></h3>
<p>: 각 인스턴스가 개별적으로 <code>getInfo</code> 메서드를 가져옴</p>
<pre><code class="language-jsx">function Animal(name, color) {
  this.name = name;
  this.color = color;
  this.getInfo = function() {
    return `이 동물의 이름은 ${this.name}이고 색깔은 ${this.color}입니다.`;
  }
}

const cat = new Animal(&quot;나비&quot;, &quot;하얀색&quot;);
const dog = new Animal(&quot;멍멍이&quot;, &quot;갈색&quot;);

console.log(cat.getInfo()); // 출력: 이 동물의 이름은 나비이고 색깔은 하얀색입니다.
console.log(dog.getInfo()); // 출력: 이 동물의 이름은 멍멍이이고 색깔은 갈색입니다.</code></pre>
<p>위 예시에서 <code>cat</code>과 <code>dog</code> 인스턴스가 각각 자신의 <code>getInfo</code> 메서드를 가져 메모리 낭비 발생</p>
<h3 id="프로토타입으로-메모리-최적화하는-예">프로토타입으로 메모리 최적화하는 예</h3>
<p>프로토타입에 <code>getInfo</code> 메서드를 추가하여 모든 인스턴스가 이를 공유하도록 개선</p>
<pre><code class="language-jsx">function Animal(name, color) {
  this.name = name;
  this.color = color;
}

// Animal의 프로토타입에 추가
Animal.prototype.getInfo = function() {
  return `이 동물의 이름은 ${this.name}이고 색깔은 ${this.color}입니다.`;
}

const cat = new Animal(&quot;나비&quot;, &quot;하얀색&quot;);
const dog = new Animal(&quot;멍멍이&quot;, &quot;갈색&quot;);

console.log(cat.getInfo()); // 출력: 이 동물의 이름은 나비이고 색깔은 하얀색입니다.
console.log(dog.getInfo()); // 출력: 이 동물의 이름은 멍멍이이고 색깔은 갈색입니다.</code></pre>
<p><code>getInfo</code> 메서드를 <strong>프로토타입에 한 번만 정의</strong>하여 <code>cat</code>과 <code>dog</code> 인스턴스가 이를 <strong>공유</strong>. 이로 인해 메모리 사용 최적화 및 코드 효율성 향상</p>
<blockquote>
<p>참고: 화살표 함수는 this가 동적으로 바인딩되지 않아 프로토타입 메서드로 적합하지 않음</p>
</blockquote>
<h2 id="프로토타입-체인과-체이닝">프로토타입 체인과 체이닝</h2>
<p><strong>프로토타입 체인</strong>: 자바스크립트의 객체 간 상속을 구현하는 메커니즘. 객체는 자신의 프로토타입을 통해 상위 객체의 속성과 메서드에 접근 가능하며, 이를 통해 상속 체계 형성</p>
<p><strong>프로토타입 체이닝:</strong> 객체의 프로퍼티나 메서드에 접근 시, 해당 객체에 원하는 프로퍼티가 없다면 객체의 프로토타입을 따라 상위 프로토타입 객체들을 차례로 검색해 나가는 과정</p>
<h3 id="proto-속성"><strong>proto</strong> 속성</h3>
<p>모든 자바스크립트 객체는 <strong><code>__proto__</code></strong> 속성을 가짐. 이 속성으로 객체의 프로토타입을 참조하고, 프로토타입 체인을 통해 상위 객체의 속성과 메서드를 상속받음.</p>
<pre><code class="language-jsx">const cat = new Animal(&quot;나비&quot;, &quot;하얀색&quot;);
console.log(cat.__proto__ === Animal.prototype); // 출력: true</code></pre>
<p><code>cat.__proto__</code>는 <code>Animal.prototype</code>을 참조하며, 이로 인해 <code>cat</code>은 <code>Animal</code>의 프로토타입에 정의된 <code>getInfo</code> 메서드 사용 가능</p>
<h3 id="예시-프로토타입-체인의-동작">예시: 프로토타입 체인의 동작</h3>
<pre><code class="language-jsx">function Car(name, color) {
  this.name = name;
  this.color = color;
}

Car.prototype.getInfo = function() {
  return `이 차의 이름은 ${this.name}이고 색깔은 ${this.color}입니다.`;
};

const car1 = new Car(&quot;택시&quot;, &quot;빨강&quot;);

console.log(car1.getInfo()); // 출력: 이 차의 이름은 택시이고 색깔은 빨강입니다.
console.log(car1.__proto__.getInfo()); // 출력: undefined, undefined</code></pre>
<p><strong><code>car1.getInfo()</code>와 <code>car1.__proto__.getInfo()</code>의 차이점</strong></p>
<ul>
<li>인스턴스 호출 (<code>car1.getInfo()</code>):<ul>
<li><code>this</code>가 <code>car1</code>을 가리킴</li>
<li><code>this.name</code>과 <code>this.color</code> 정상 출력</li>
</ul>
</li>
<li>프로토타입 직접 호출 (<code>car1.__proto__.getInfo()</code>):<ul>
<li><code>this</code>가 <code>Car.prototype</code>을 가리킴</li>
<li><code>name</code>과 <code>color</code> 속성 없어 <code>undefined</code> 출력</li>
</ul>
</li>
</ul>
<p>이는 프로토타입 체인과 <code>this</code> 바인딩의 중요한 특성을 보여줌</p>
<h3 id="프로토타입-체인의-끝-objectprototype">프로토타입 체인의 끝: Object.prototype</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/1c8ea34c-e6a4-4429-a060-2946f862346b/image.png" /></p>
<p>모든 객체는 최상위 프로토타입인 <strong><code>Object.prototype</code></strong> 까지 프로토타입 체인을 통해 연결됨<code>Object.prototype</code>은 모든 객체가 공통으로 사용하는 메서드들이 정의된 곳. 프로토타입 체인을 따라 상위 객체가 계속 연결되다가, <code>Object.prototype</code>에서 끝이 나며, 이 다음에는 <code>null</code>이 존재</p>
<pre><code class="language-jsx">console.log(Object.prototype.__proto__); // 출력: null</code></pre>
<h3 id="💡-프로토타입-이해를-통해-얻은-중요-인사이트">💡 프로토타입 이해를 통해 얻은 중요 인사이트</h3>
<p><code>hasOwnProperty</code> 메소드 사용은 객체의 인스턴스 특성에 기인. 인스턴스는 프로토타입 체인을 통해 상위 객체의 속성과 메소드에 접근 가능</p>
<p>이는 단순 객체 특성이 아닌, 인스턴스만의 고유한 성질</p>
<ul>
<li>생성자 함수로 만든 인스턴스는 부모 프로토타입을 상속받음. 이 프로토타입 역시 다른 객체의 인스턴스</li>
<li>개발자 도구에서 프로토타입의 <strong><strong>proto</strong></strong> 속성을 통해 확인 가능</li>
</ul>
<hr />
<h2 id="인스턴스">인스턴스</h2>
<p><strong><code>인스턴스</code></strong>: 생성자 함수와 <code>new</code> 키워드로 만든 객체. 생성자 함수 내 <code>this</code>로 정의된 속성 포함. 프로토타입 상속받아 그 속성과 메서드 사용 가능함</p>
<h3 id="인스턴스의-주요-특징">인스턴스의 주요 특징</h3>
<ul>
<li><strong>멤버 속성</strong>: 생성자 함수 내 <code>this</code>로 정의된 인스턴스 고유 속성<ul>
<li><code>this.name = name;</code>으로 설정된 속성은 각 인스턴스의 멤버 속성</li>
<li>각 인스턴스는 독립적인 멤버 속성과 고유 값 보유</li>
</ul>
</li>
<li><strong><code>__proto__</code></strong> 속성으로 부모 프로토타입 객체 접근</li>
</ul>
<blockquote>
<p>주의: 생성자 함수 내 <code>let</code>/<code>const</code> 변수는 지역 변수로, 인스턴스에 포함되지 않음</p>
</blockquote>
<pre><code class="language-jsx">function Car(name) {
    this.name = name;
}

const car1 = new Car(&quot;택시&quot;);
console.log(car1.name); // 출력: 택시
console.log(car1.__proto__ === Car.prototype); // 출력: true</code></pre>
<p><code>car1.name</code>은 &quot;<strong>멤버 속성&quot;</strong>임. <code>car1.__proto__</code>는 <code>Car.prototype</code> 참조. 인스턴스가 고유 속성을 가지면서 동시에 생성자 함수의 프로토타입 상속받음을 보여줌</p>
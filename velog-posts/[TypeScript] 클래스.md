<h2 id="1-타입스크립트-클래스의-특징">1. 타입스크립트 클래스의 특징</h2>
<p>타입스크립트 클래스는 자바스크립트 클래스와 비슷한 구조를 가지며, 다음과 같은 차이점을 보유</p>
<ol>
<li><strong>타입 지정 가능</strong>: 속성과 메서드에 타입 명시 가능</li>
<li><strong>접근 제어자</strong>: <code>public</code>, <code>protected</code>, <code>private</code> 키워드로 멤버의 접근 범위 제어 가능</li>
<li><strong>추상 클래스 지원</strong>: 추상 메서드와 멤버를 포함 가능하며, 상속받는 클래스에서 구현 필요</li>
</ol>
<hr />
<h2 id="2-접근-제어자-public-protected-private">2. 접근 제어자 (Public, Protected, Private)</h2>
<p>타입스크립트는 클래스 멤버에 <strong>접근 제어자</strong> 사용 가능</p>
<h3 id="접근-제어자의-종류">접근 제어자의 종류</h3>
<ul>
<li><strong><code>public</code> (기본값)</strong>: 어디서든 접근 가능</li>
<li><strong><code>protected</code></strong>: 해당 클래스와 하위 클래스에서만 접근 가능</li>
<li><strong><code>private</code></strong>: 해당 클래스 내에서만 접근 가능</li>
</ul>
<pre><code class="language-tsx">class Car {
  public model: string; // 어디서나 접근 가능
  protected speed: number; // 해당 클래스와 하위 클래스에서만 접근 가능
  private year: number; // 클래스 내부에서만 접근 가능

  constructor(model: string, speed: number, year: number) {
    this.model = model;
    this.speed = speed;
    this.year = year;
  }

  private getYear(): number {
    return this.year;
  }
}

class Benz extends Car {
  constructor(model: string, speed: number, year: number) {
    super(model, speed, year);
  }

  maxSpeed(): number {
    return this.speed + 50; // protected 멤버 접근 가능
  }
}

const car = new Benz(&quot;Benz&quot;, 200, 2020);
console.log(car.model); // ✅ &quot;Benz&quot;
// console.log(car.speed); // ❌ protected 멤버에 직접 접근 불가
// console.log(car.year); // ❌ private 멤버에 직접 접근 불가</code></pre>
<h2 id="3-추상-클래스">3. 추상 클래스</h2>
<p><strong>추상 클래스</strong>는 직접적으로 인스턴스 생성 불가</p>
<p>특정 클래스에서 구현해야 되는 걸 미리 정의할 때 사용</p>
<p><strong><code>abstract</code> 키워드로 추상 클래스와 추상 멤버를 선언</strong></p>
<ul>
<li><strong>추상(<code>abstract</code>) 멤버</strong>: 상속받는 클래스에서 반드시 구현 필요</li>
<li><strong>일반 멤버</strong>: 추상 클래스 내에서 이미 구현되어 있어 상속받는 클래스에서 선택적 오버라이드 가능</li>
</ul>
<pre><code class="language-tsx">abstract class Animal {
  // abstract 멤버: 반드시 구현해야 함
  abstract makeSound(): void;

  // 일반 멤버: 이미 구현되어 있음
  eat(): void {
    console.log('먹는 중...');
  }
}</code></pre>
<h3 id="추상-클래스-예제">추상 클래스 예제</h3>
<pre><code class="language-tsx">abstract class CarAbstract {
  abstract name: string;
  abstract color: string;
  abstract start(): void; // 구현 강제
  printInfo(): void {
    console.log(`${this.name}, ${this.color}`); // 구현된 메서드
  }
}

class Car extends CarAbstract {
  name: string;
  color: string;

  constructor(name: string, color: string) {
    super(); //상속
    this.name = name;
    this.color = color;
  }

  start(): void {
    console.log(`${this.name} is starting...`);
  }
}

const car = new Car(&quot;BMW&quot;, &quot;Red&quot;);
car.start(); // &quot;BMW is starting...&quot;
//특정 메서드를 미리 완성시켜 두고 호출 가능
car.printInfo(); // &quot;BMW, Red&quot;</code></pre>
<hr />
<h2 id="4-인터페이스-구현-implements">4. 인터페이스 구현 (Implements)</h2>
<p><strong>인터페이스</strong>는 클래스가 따라야 할 <strong>규칙(타입)</strong>을 정의</p>
<p>타입스크립트의 클래스는 <strong><code>implements</code></strong> 키워드로 인터페이스 구현 가능</p>
<h3 id="인터페이스-구현-예제">인터페이스 구현 예제</h3>
<pre><code class="language-tsx">interface Moveable {
  speed: number;
  move(): void;
}

interface Drivable {
  drive(): void;
}

class Car implements Moveable, Drivable {
  speed: number;

  constructor(speed: number) {
    this.speed = speed;
  }

  move(): void {
    console.log(&quot;Moving...&quot;);
  }

  drive(): void {
    console.log(&quot;Driving...&quot;);
  }
}

const car = new Car(100);
car.move(); // &quot;Moving...&quot;
car.drive(); // &quot;Driving...&quot;</code></pre>
<blockquote>
<p>💡 차이점:</p>
<ul>
<li><strong>추상 클래스</strong>는 구현된 메서드와 속성 포함 가능, <strong>인터페이스</strong>는 메서드와 속성의 형태만 정의</li>
</ul>
</blockquote>
<hr />
<h2 id="5-제네릭-클래스">5. 제네릭 클래스</h2>
<ul>
<li><strong>제네릭(Generic)</strong>을 클래스에 적용 시 클래스가 다양한 타입의 데이터 처리 가능</li>
</ul>
<h3 id="제네릭-클래스-기본-예제">제네릭 클래스 기본 예제</h3>
<pre><code class="language-tsx">class Box&lt;T&gt; {
  value: T;

  constructor(value: T) {
    this.value = value;
  }

  getValue(): T {
    return this.value;
  }
}

const stringBox = new Box&lt;string&gt;(&quot;Hello&quot;);
console.log(stringBox.getValue()); // &quot;Hello&quot;

const numberBox = new Box&lt;number&gt;(123);
console.log(numberBox.getValue()); // 123</code></pre>
<h3 id="제네릭-클래스-상속">제네릭 클래스 상속</h3>
<pre><code class="language-tsx">class Container&lt;T&gt; {
  value: T;

  constructor(value: T) {
    this.value = value;
  }

  getValue(): T {
    return this.value;
  }
}

class StringContainer extends Container&lt;string&gt; {
  constructor(value: string) {
    super(value);
  }

  print(): void {
    console.log(&quot;문자열 컨테이너 값:&quot;, this.value);
  }
}

const strContainer = new StringContainer(&quot;타입스크립트&quot;);
strContainer.print(); // &quot;문자열 컨테이너 값: 타입스크립트&quot;</code></pre>
<h2 id="6-클래스-상속">6. 클래스 상속</h2>
<pre><code class="language-tsx">class Vehicle {
  wheels: number;

  constructor(wheels: number) {
    this.wheels = wheels;
  }

  drive(): void {
    console.log(`Driving with ${this.wheels} wheels.`);
  }
}

class Car extends Vehicle {
  constructor() {
    super(4); // 부모 클래스의 생성자 호출
  }

  drift(): void {
    console.log(&quot;Drifting...&quot;);
  }
}

const car = new Car();
car.drive(); // &quot;Driving with 4 wheels.&quot;
car.drift(); // &quot;Drifting...&quot;</code></pre>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>
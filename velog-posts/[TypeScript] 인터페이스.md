<p>인터페이스는 TypeScript에서 객체 타입을 정의하는 데 최적화된 문법임. 타입 별칭이 변수를 할당하는 듯한 느낌을 주는 반면, 인터페이스는 클래스 문법과 유사하게 중괄호를 열어 바로 선언함</p>
<hr />
<h2 id="1-인터페이스의-기본-사용">1. 인터페이스의 기본 사용</h2>
<p>인터페이스는 객체의 타입을 지정할 때 사용됨</p>
<pre><code class="language-tsx">interface Person {
  name: string;
  age: number;
}

const user: Person = {
  name: &quot;Alice&quot;,
  age: 30,
};</code></pre>
<h2 id="2-객체-속성-기법">2. 객체 속성 기법</h2>
<h3 id="선택적-속성-optional">선택적 속성 (Optional)</h3>
<pre><code class="language-tsx">interface User {
  name: string;
  age: number;
  email?: string; // 선택적 속성
}

const user1: User = { name: &quot;Alice&quot;, age: 30 }; // ✅ OK
const user2: User = { name: &quot;Bob&quot;, age: 25, email: &quot;bob@example.com&quot; }; // ✅ OK</code></pre>
<h3 id="읽기-전용-속성-readonly">읽기 전용 속성 (Readonly)</h3>
<pre><code class="language-tsx">interface ReadonlyUser {
  readonly id: number;
  name: string;
  age: number;
}

const user: ReadonlyUser = { id: 1, name: &quot;Alice&quot;, age: 30 };
// user.id = 2; // ❌ 오류: 'id'는 읽기 전용임</code></pre>
<h2 id="3-인덱스-시그니처">3. 인덱스 시그니처</h2>
<p>객체의 키와 값을 동적으로 정의할 수 있음</p>
<pre><code class="language-tsx">interface StringDict {
  [key: string]: string;
}

const dict: StringDict = {
  name: &quot;Alice&quot;,
  city: &quot;Seoul&quot;,
};</code></pre>
<h2 id="4-함수-타입">4. 함수 타입</h2>
<p>인터페이스를 사용해 함수 타입도 정의 가능</p>
<pre><code class="language-tsx">interface MathFunc {
  (x: number, y: number): number;
}

const add: MathFunc = (a, b) =&gt; a + b;
const multiply: MathFunc = (a, b) =&gt; a * b;

console.log(add(5, 3));      // 출력: 8
console.log(multiply(4, 2)); // 출력: 8</code></pre>
<p>하지만 이 방식은 직관적이지 않아 실무에서 인터페이스로 함수 타입을 지정하는 경우가 거의 없음. 대신 타입 별칭이 더 편리하고 가독성이 높아 선호됨</p>
<blockquote>
<p>타입 별칭을 사용한 함수 타입 정의</p>
</blockquote>
<pre><code class="language-tsx">type MathFunction = (x: number, y: number) =&gt; number;</code></pre>
<h2 id="5-선언병합declaration-merging">5. 선언병합(Declaration Merging)</h2>
<p>동일한 이름의 인터페이스를 여러 번 선언할 경우 이들이 자동으로 병합되어 하나의 인터페이스로 통합됨</p>
<p>인터페이스는 코드 작성 위치에 관계없이 병합됨. 이는 타입스크립트의 정적 타입 시스템의 특징 중 하나임</p>
<pre><code class="language-jsx">interface User {
    name: string;
    age: number;
  }

  interface User {
    address: string;
  }

  let user: User = {
    name: &quot;Alice&quot;,
    age: 30,
    address: &quot;Seoul&quot;,
  };</code></pre>
<h2 id="타입별칭-비교">타입별칭 비교</h2>
<h3 id="중복-식별자">중복 식별자</h3>
<pre><code class="language-jsx">type UserType = {
  name: string;
  age: number;
};

// ❌ Error
type UserType = {
  address: string;
};</code></pre>
<p>선언 병합은 인터페이스의 주요 단점 중 하나로, 협업 시 예상치 못한 오류를 일으킬 수 있음.</p>
<p>실무에선 일반적으로 객체 타입은 interface로, 기타 커스텀 타입은 type 별칭으로 지정함</p>
<p>✅ 하지만 인터페이스로도 함수 타입 지정이 가능함(강사님 선호)</p>
<h3 id="자동완성-툴팁">자동완성 툴팁</h3>
<p>타입별칭: 자동완성 툴팁에서 더 상세한 정보 제공. 인터페이스: 기본적인 타입 정보만 표시하는 경향. 복잡한 객체 구조에서 덜 상세할 수 있음</p>
<pre><code class="language-tsx">type User = {
  name: string;
  age: number;
  email: string;
};

//마우스를 올려보면 속성이 툴팁으로 보임
const user: User = {
  // 여기서 속성을 입력할 때 자동완성 툴팁이 제공됨
  name: &quot;Alice&quot;,
  age: 30,
  email: &quot;alice@example.com&quot;
};

// user. 을 입력하면 name, age, email 속성에 대한 자세한 정보가 툴팁으로 표시됨
console.log(user.name);</code></pre>
<h2 id="5-인터페이스의-상속">5. 인터페이스의 상속</h2>
<p>인터페이스: 다른 인터페이스를 상속받아 확장 가능</p>
<pre><code class="language-tsx">interface Shape {
  color: string;
}

interface Circle extends Shape {
  radius: number;
}

const myCircle: Circle = {
  color: &quot;red&quot;,
  radius: 10,
};</code></pre>
<p><strong><code>타입 별칭</code>을 사용한 인터페이스 확장</strong></p>
<pre><code class="language-jsx">interface Shape {
  color: string;
}

interface Circle {
  radius: number;
}

type CircleShape = Shape &amp; Circle;

const myCircle: CircleShape = {
  color: &quot;red&quot;,
  radius: 5,
};

console.log(myCircle.color);  // 출력: red
console.log(myCircle.radius); // 출력: 5</code></pre>
<h3 id="다중-상속-패턴">다중 상속 패턴</h3>
<pre><code class="language-jsx">interface Person {
    name: string;
    age: number;
  }

  const person: Person = {
    name: &quot;John&quot;,
    age: 20,
  };

  interface Address {
    city: string;
    readonly zipCode?: string;
  }

  interface Employee extends Person, Address {
    employeeId: string;
  }

  const employee: Employee = {
    name: &quot;kisu&quot;,
    age: 20,
    employeeId: &quot;1234&quot;,
    city: &quot;seuol&quot;,
    zipCode: &quot;131111&quot;,
  };</code></pre>
<h3 id="상속-예제">상속 예제</h3>
<pre><code class="language-jsx">interface Animal {
  name?: string;
  sound(): void; // sound: () =&gt; void
}

interface Pet extends Animal {
  play?(): void; // play: () =&gt; void
}

// 단축 메서드명
const dog: Pet = {
  name: &quot;뽀삐&quot;,
  sound() {
    console.log(&quot;멍멍&quot;);
  },
  play() {
    console.log(&quot;놀기&quot;);
  },
};

if (dog.play) dog.play();</code></pre>
<p>마지막 줄의 if 문은 타입가드</p>
<pre><code class="language-tsx">if (dog.play) dog.play();</code></pre>
<p>이렇게 함으로써, play 메서드가 존재할 때만 호출되어 더 안전한 코드 실행이 가능해짐</p>
<h2 id="6-인터페이스-제네릭">6. 인터페이스 제네릭</h2>
<pre><code class="language-tsx">interface Box&lt;T&gt; {
  contents: T;
}

const numberBox: Box&lt;number&gt; = { contents: 42 };
const stringBox: Box&lt;string&gt; = { contents: &quot;Hello, TypeScript!&quot; };</code></pre>
<h3 id="고급-사용-패턴-제네릭--상속">고급 사용 패턴: 제네릭 + 상속</h3>
<pre><code class="language-tsx"> //1. Container 인터페이스 정의: 제네릭 T를 사용해 value 속성을 정의
 interface Container&lt;T&gt; {
    value: T;
  }

//2. Box 인터페이스 정의: Container&lt;U&gt;를 상속받고, 추가적으로 scale과 inStock 속성을 정의
  interface Box&lt;T, U&gt; extends Container&lt;U&gt; {
    label: string;
    scale?: T;
    inStock?: U;
  }

//3. Container 타입 객체 생성: number 타입의 value를 가지는 container 객체
  const container: Container&lt;number&gt; = {
    value: 10,
  };

//4. Box 타입 객체 생성: number 타입의 scale과 boolean 타입의 inStock을 가지는 box 객체
  const box: Box&lt;number, boolean&gt; = {
    label: &quot;grid box&quot;,
    value: true, // value는 boolean (Container&lt;U&gt;에서 상속됨)
    scale: 10, // scale은 number (Box&lt;T&gt;에서 정의됨)
  };</code></pre>
<h2 id="인터페이스와-타입별칭의-차이점">인터페이스와 타입별칭의 차이점</h2>
<table>
<thead>
<tr>
<th><strong>구분</strong></th>
<th><strong>인터페이스</strong></th>
<th><strong>타입별칭</strong></th>
</tr>
</thead>
<tbody><tr>
<td>객체 타입 정의</td>
<td>주로 사용</td>
<td>가능</td>
</tr>
<tr>
<td>함수, 유니온, 인터섹션</td>
<td>제한적 사용 가능 (함수 타입 지정 가능하나 실무에서 잘 사용하지 않음)</td>
<td>가능 (더 편리하고 가독성이 높아 선호됨)</td>
</tr>
<tr>
<td>선언 병합</td>
<td>지원 (동일한 이름의 인터페이스를 여러 번 선언 시 자동으로 병합)</td>
<td>지원하지 않음 (중복 선언 시 오류 발생)</td>
</tr>
<tr>
<td>상속</td>
<td>extends 키워드로 다중 상속 가능</td>
<td>&amp; 연산자로 타입 확장 가능</td>
</tr>
<tr>
<td>자동완성 툴팁</td>
<td>기본적인 타입 정보만 표시</td>
<td>더 상세한 정보 제공</td>
</tr>
<tr>
<td>제네릭</td>
<td>지원</td>
<td>지원</td>
</tr>
</tbody></table>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>
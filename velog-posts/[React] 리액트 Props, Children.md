<p><strong><code>리액트</code></strong>는 부모에서 → 자식 컴포넌트에게만 데이터를 전달할 수 있음  <strong>⇒ 단방향 데이터 흐름</strong></p>
<blockquote>
<p>💡 반면 <strong>Vue</strong>는 양방향 데이터 바인딩을 지원</p>
</blockquote>
<hr />
<h2 id="props-부모-→-자식-데이터-전달">Props: 부모 → 자식 데이터 전달</h2>
<p><strong><code>Props</code></strong>는 부모 컴포넌트가 자식 컴포넌트로 데이터를 전달할 때 사용</p>
<p>전달받은 데이터는 자식 컴포넌트에서 수정 불가능함</p>
<p>Props는 <strong>객체 형태로 전달</strong>되며, 컴포넌트에 사용된 모든 속성들은 하나의 props 객체로 모아짐</p>
<p><strong>예제</strong></p>
<pre><code class="language-tsx">// 부모 컴포넌트
&lt;Child name=&quot;James&quot; age={25} /&gt;

// 자식 컴포넌트에서는 하나의 props 객체로 받음
function Child(props) {
  console.log(props); // { name: &quot;James&quot;, age: 25 }
  return &lt;div&gt;{props.name}&lt;/div&gt;;
}</code></pre>
<p><strong>Props의 기본 문법</strong></p>
<pre><code class="language-tsx">&lt;Component 속성={값} /&gt;</code></pre>
<h3 id="props-예제"><strong>Props 예제</strong></h3>
<p><strong>부모 컴포넌트에서 데이터 전달</strong></p>
<pre><code class="language-tsx">// App.tsx
import Child from &quot;./components/Child&quot;;

export default function App() {
  return (
    &lt;&gt;
      &lt;h1&gt;App&lt;/h1&gt;
      {/* props 객체로 전달 */}
      &lt;Child
        name=&quot;James&quot;
        age={10}
        foods={[&quot;apple&quot;, &quot;banana&quot;]}
        address={{ zipcode: 1112, city: &quot;Seoul&quot; }}
      /&gt;
    &lt;/&gt;
  );
}</code></pre>
<p><strong>자식 컴포넌트에서 Props 수신</strong></p>
<p>Props를 받을 때 매개변수명으로 'props'를 사용하는 것이 React에서의 일반적인 관례</p>
<pre><code class="language-tsx">// Child.tsx
export default function Child(props: { //부모 컴포넌트로부터 전달된 props를 받음
  name: string;
  age: number;
  foods: string[];
  address: { zipcode: number; city: string };
}) {
  return (
    &lt;div&gt;
      &lt;h1&gt;{props.name}&lt;/h1&gt;
      &lt;h1&gt;{props.age}&lt;/h1&gt;
      &lt;h1&gt;{props.foods[0]}&lt;/h1&gt;
      &lt;h1&gt;{props.address.city}&lt;/h1&gt;
    &lt;/div&gt;
  );
}</code></pre>
<h3 id="props를-interface로-관리하기">Props를 Interface로 관리하기</h3>
<p>더 복잡한 프로젝트에서는 <strong><code>Interface</code></strong>를 사용하여 Props를 정의함</p>
<blockquote>
<p>💡 ChildPropsType은 컴포넌트의 props 타입을 정의할 때 일반적으로 사용되는 규칙</p>
</blockquote>
<pre><code class="language-tsx">// Child.tsx
interface ChildPropsType {
  name: string;
  age: number;
  foods: string[];
  address: { zipcode: number; city: string };
}

export default function Child(props: ChildPropsType) {
  return (
    &lt;div&gt;
      &lt;h1&gt;{props.name}&lt;/h1&gt;
      &lt;h1&gt;{props.age}&lt;/h1&gt;
      &lt;h1&gt;{props.foods[0]}&lt;/h1&gt;
      &lt;h1&gt;{props.address.city}&lt;/h1&gt;
    &lt;/div&gt;
  );
}</code></pre>
<h3 id="props-타입-파일-분리하기">Props 타입 파일 분리하기</h3>
<p>큰 프로젝트에서 Props 타입을 별도 파일로 분리하여 관리하면 효율적</p>
<p>여러 컴포넌트의 타입을 한 곳에서 관리 가능</p>
<p>타입 정의 파일(<code>.d.ts</code>) 특징:</p>
<ul>
<li>TypeScript의 <strong>전역 타입 정의</strong> 파일</li>
<li>타입 정보만 제공 (JavaScript 변환 X)</li>
<li>src 폴더에서 자동 인식</li>
</ul>
<blockquote>
<p>💡 <code>props.d.ts</code> 파일은 import 없이 전역에서 사용 가능</p>
</blockquote>
<pre><code class="language-tsx">// src/types/props.d.ts
export interface ChildPropsType {
  name: string;
  age: number;
}

// Child.tsx
import { ChildPropsType } from './types';

export default function Child({ name, age }: ChildPropsType) {
  // ...
}</code></pre>
<h3 id="props-객체를-구조-분해-할당하기">Props 객체를 구조 분해 할당하기</h3>
<p>Props 객체를 구조 분해하여 코드를 간결하게 작성 가능함</p>
<blockquote>
<p>💡 객체는 JSX 표현식에서 직접 출력할 수 없음 ⇒ <code>JSON.stringify()</code>를 사용하여 문자열로 변환</p>
</blockquote>
<pre><code class="language-tsx">export default function Child({ name, age, foods, address }: ChildPropsType) {
  return (
    &lt;div&gt;
      &lt;h1&gt;{name}&lt;/h1&gt;
      &lt;h1&gt;{age}&lt;/h1&gt;
      &lt;h1&gt;{foods[0]}&lt;/h1&gt;
      &lt;h1&gt;{JSON.stringify(address)}&lt;/h1&gt;
    &lt;/div&gt;
  );
}</code></pre>
<p>혹은 함수 내부에서 타입 지정과 함께 구조분해할당을 할 수도 있음</p>
<pre><code class="language-tsx">export default function Child(props: ChildPropsType) {
  const {
    name,
    age,
    foods,
    address: { zipcode, city },
  } = props;
  return (
    &lt;div className=&quot;text-3xl font-bold&quot;&gt;
      &lt;h1&gt;{name}&lt;/h1&gt;
      &lt;h1&gt;{age}&lt;/h1&gt;
      &lt;h1&gt;{foods[0]}&lt;/h1&gt;
      &lt;h1&gt;{foods[1]}&lt;/h1&gt;
      &lt;h1&gt;{zipcode}&lt;/h1&gt;
      &lt;h1&gt;{city}&lt;/h1&gt;
    &lt;/div&gt;
  );
}</code></pre>
<h3 id="props의-기본값-설정">Props의 기본값 설정</h3>
<p>Props에 기본값 지정 가능. <code>age</code> 값 미전달 시 기본값 <code>30</code> 설정됨</p>
<pre><code class="language-tsx">export default function Child({ name, age = 30 }: { name: string; age?: number }) {
  return (
    &lt;div&gt;
      &lt;h1&gt;{name}&lt;/h1&gt;
      &lt;h1&gt;{age}&lt;/h1&gt;
    &lt;/div&gt;
  );
}</code></pre>
<hr />
<h2 id="children-태그-사이-내용-전달">Children: 태그 사이 내용 전달</h2>
<p><strong>Children</strong>은 컴포넌트 태그 사이의 내용을 자식 컴포넌트에 전달할 때 사용</p>
<p><strong>컴포넌트당 하나만 존재</strong>하며, 컴포넌트 태그 사이에 위치한 모든 JSX 요소를 포함</p>
<p>Children은 <code>children</code>이라는 고정된 키값을 사용</p>
<h3 id="children-기본-사용법">Children 기본 사용법</h3>
<pre><code class="language-tsx">// App.tsx
export default function App() {
  return (
    &lt;&gt;
      &lt;h1&gt;App&lt;/h1&gt;
      &lt;Child&gt;
        &lt;h2&gt;이것이 Children입니다&lt;/h2&gt;
      &lt;/Child&gt;
    &lt;/&gt;
  );
}</code></pre>
<pre><code class="language-tsx">// Child.tsx
export default function Child({ children }: { children: React.ReactNode }) {
  return &lt;div&gt;{children}&lt;/div&gt;;
}</code></pre>
<h3 id="reactnode와-reactelement">ReactNode와 ReactElement</h3>
<ul>
<li><strong>ReactNode</strong>: 모든 React 요소를 포함하는 타입 (string, number, JSX, null 등)</li>
<li><strong>ReactElement</strong>: JSX 요소만 포함하는 타입</li>
</ul>
<p>ReactNode는 더 넓은 범위를 커버하므로 Children의 타입으로 주로 사용</p>
<hr />
<h2 id="props-vs-children의-차이점">Props vs Children의 차이점</h2>
<table>
<thead>
<tr>
<th><strong>특징</strong></th>
<th><strong>Props</strong></th>
<th><strong>Children</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>전달 방식</strong></td>
<td>부모 → 자식</td>
<td>태그 사이에 JSX로 전달</td>
</tr>
<tr>
<td><strong>사용 목적</strong></td>
<td>단순 데이터 전달</td>
<td>마크업 구조 전달</td>
</tr>
<tr>
<td><strong>유연성</strong></td>
<td>제한적</td>
<td>더 복잡한 구조 전달 가능</td>
</tr>
</tbody></table>
<p><strong>예제</strong></p>
<h3 id="props로-데이터-전달">Props로 데이터 전달</h3>
<pre><code class="language-tsx">&lt;Child content=&quot;&lt;h1&gt;Hello&lt;/h1&gt;&quot; /&gt;</code></pre>
<ul>
<li>문자열로 전달되어 JSX 구조로 인식되지 않음</li>
</ul>
<h3 id="children으로-데이터-전달">Children으로 데이터 전달</h3>
<pre><code class="language-tsx">&lt;Child&gt;
  &lt;h1&gt;Hello&lt;/h1&gt;
&lt;/Child&gt;</code></pre>
<ul>
<li>JSX 구조 그대로 전달됨</li>
</ul>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>
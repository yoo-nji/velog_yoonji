<p><strong><code>메서드 체이닝이란?</code></strong> 하나의 객체 메서드를 연결해서 연속적으로 호출하는 기법.</p>
<h3 id="메서드-체이닝의-핵심-원리">메서드 체이닝의 핵심 원리</h3>
<p>각 메서드가 <strong>객체 자신</strong>을 반환하여 연속 호출 가능.</p>
<h3 id="주요-이점"><strong>주요 이점</strong></h3>
<ul>
<li><strong>연속 호출:</strong> 객체 반환으로 즉시 다음 메서드 호출</li>
<li><strong>가독성 향상:</strong> 여러 작업을 한 줄로 연결, 간결성 증대</li>
<li><strong>유연성:</strong> 필요한 메서드만 선택적 연결 가능</li>
</ul>
<h3 id="메서드-체이닝-구현-방법"><strong>메서드 체이닝 구현 방법</strong></h3>
<ul>
<li><strong>메서드 정의:</strong> 각 메서드에서 작업 수행 후 <code>this</code> 반환</li>
<li><strong>메서드 연결:</strong> 객체 생성 후 점(.) 연산자로 메서드 연속 호출</li>
<li><strong>최종 결과:</strong> 체인의 마지막에 결과를 반환하는 메서드 호출</li>
</ul>
<p><strong>예제</strong></p>
<pre><code class="language-jsx">class 계산기 {
  constructor() {
    this.값 = 0;
  }

  더하기(숫자) {
    this.값 += 숫자;
    return this; // 객체 자신을 반환하여 체이닝 가능하게 함
  }

  빼기(숫자) {
    this.값 -= 숫자;
    return this;
  }

  곱하기(숫자) {
    this.값 *= 숫자;
    return this;
  }

  결과얻기() {
    return this.값; // 최종 값을 반환
  }
}

const 결과 = new 계산기()
  .더하기(5)
  .빼기(2)
  .곱하기(3)
  .결과얻기();

console.log(결과); // 출력: 9</code></pre>
<p>위 예제에서 <code>더하기</code>, <code>빼기</code>, <code>곱하기</code> 메서드는 모두 <code>this</code> 반환. 계산기 객체에 연속적인 메서드 호출 가능. 마지막으로 <code>결과얻기</code> 호출하여 최종 계산된 값 반환</p>
<h3 id="메서드-체이닝을-단계별로-이해하기">메서드 체이닝을 단계별로 이해하기</h3>
<pre><code class="language-jsx">javascript
코드 복사
const 계산기 = new 계산기();
계산기.더하기(5);  // 5를 더하고 계산기 객체 반환
계산기.빼기(2);    // 2를 빼고 계산기 객체 반환
계산기.곱하기(3);  // 3을 곱하고 계산기 객체 반환
const 결과 = 계산기.결과얻기();  // 최종 결과 얻기</code></pre>
<p>각 메서드가 <code>this</code> 반환함으로써 메서드 체이닝 가능. 코드의 간결성과 가독성 향상</p>
<h3 id="요약">요약</h3>
<ul>
<li>메서드 체이닝: 객체 메서드 호출을 연속적으로 이어서 표현 가능한 기법</li>
<li>각 메서드는 <code>this</code> 반환하여 다음 메서드 바로 호출 가능</li>
<li>코드의 간결성과 가독성 향상. 선택적 메서드 연결로 유연한 사용 가능</li>
</ul>
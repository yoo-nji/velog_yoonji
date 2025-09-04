<blockquote>
<p>글 업로드 할 때 이미지 프리뷰를 보여주기위해서는 <strong><code>URL.createObjectURL</code> vs <code>FileReader.readAsDataURL</code></strong> 두 가지 방법을 활용할 수 있다. 이걸 비교해 보고자 한다</p>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/05aa4aad-6aec-4f08-b541-d50693ad6f94/image.png" /></p>
<h2 id="1-비교하기">1. 비교하기</h2>
<h3 id="1-1-데이터-형식">1-1. 데이터 형식</h3>
<ul>
<li><strong><code>URL.createObjectURL</code></strong>: 브라우저 메모리 내 객체를 참조하는 <strong>임시 blob URL</strong> 생성
ex) blob:<a href="https://example.com/550e8400">https://example.com/550e8400</a>...<ul>
<li>이 URL은 <strong>현재 브라우저 탭/세션 내에서만 유효</strong>, 새로고침하거나 탭 닫으면 사라짐</li>
<li><strong>장점:</strong> base64 변환이 필요 없어서 빠르고 메모리 효율적.</li>
<li><strong>단점:</strong> <strong>외부 저장 불가</strong>. 서버로 보내거나 LocalStorage에 그대로 보관할 수 없음. 
(서버에 보내려면 원본 Blob/File을 직접 FormData로 append해서 보내야 함)<ul>
<li><strong>주의:</strong> 사용 끝나면 URL.revokeObjectURL(url)로 <strong>직접 해제</strong> 필요(이후 예제 참고)</li>
</ul>
</li>
</ul>
</li>
<li><strong><code>FileReader.readAsDataURL</code></strong>: 파일 내용을 <strong>base64 문자열</strong>로 변환해 &quot;data:...&quot; 형식으로 생성
ex) data:image/jpeg;base64,/9j/4AAQSkZJRgAB...<ul>
<li><strong>장점:</strong> 브라우저의 메모리 <strong>외부에서도 사용 가능</strong>. ⇒ 로컬 스토리지에 저장, 서버 전송, 다른 컨텍스트(다른 탭, 다른 브라우저)에서도 그대로 사용 가능</li>
<li><strong>단점:</strong> base64 인코딩이라 용량이 33% 정도 커지고 메모리 소모도 큼.</li>
</ul>
</li>
</ul>
<h3 id="1-2-시간">1-2. 시간</h3>
<ul>
<li><strong><code>URL.createObjectURL</code></strong>: 동기적으로 실행(즉시 실행)</li>
<li><strong><code>FileReader.readAsDataURL</code></strong>은 비동기적으로 실행(시간이 조금 지체된 후 실행)</li>
</ul>
<h3 id="1-3-메모리">1-3. 메모리</h3>
<ul>
<li><strong><code>URL.createObjectURL</code></strong> : <strong>직접 revokeObjectURL로 해제 필요</strong>(또는 문서 종료 시 해제)</li>
<li><strong><code>FileReader.readAsDataURL</code></strong> : 결과가 긴 문자열이라(base64) Blob URL(createObjectURL)에 비해 메모리를 많이 잡아먹지만, 사용하지 않으면 자동으로 <strong>가비지 컬렉터에 의해 자동 제거</strong></li>
</ul>
<h3 id="1-4-지원">1-4. 지원</h3>
<ul>
<li>두 방식 모두 <strong>IE10+ 및 모던 브라우저</strong> OK.</li>
</ul>
<h3 id="1-5-결론">1-5. 결론</h3>
<ul>
<li><strong>미리보기(Preview)</strong> 용도라면 createObjectURL이 <strong>가볍고 빠름.
단,</strong> 사용하지 않을 때 일일이 <strong>revokeObjectURL</strong>로 release시켜주어야 하는 번거로움이 있다.</li>
<li><strong>Base64(data URL)</strong> 은 “문자열이 필요할 때” 쓰면 좋음. (예: LocalStorage 임시 저장/복사-붙여넣기/서버가 Base64만 받을 때)</li>
<li><em>이미지 크기 커질수록 손해(33%↑)*</em> 이고, <strong>인코딩 CPU/메모리 비용</strong>도 들기 때문에 <strong>createObjectURL</strong>을 권장한다고 함. gpt왈</li>
</ul>
<h2 id="2-예제-코드">2. 예제 코드</h2>
<h4 id="urlcreateobjecturl-urlrevokeobjecturl"><strong><code>URL.createObjectURL</code>, <code>URL.revokeObjectURL</code></strong></h4>
<pre><code class="language-tsx">import { useEffect, useRef, useState } from &quot;react&quot;;

export default function ImagePreview() {
  const [previewUrl, setPreviewUrl] = useState&lt;string | null&gt;(null);

  const handleChangeImage = (e: React.ChangeEvent&lt;HTMLInputElement&gt;) =&gt; {
    const file = e.target.files?.[0];
    if (!file) return;

    // 새 URL 만들기 전에 이전 URL 해제
    setPreviewUrl((prev) =&gt; {
      if (prev) URL.revokeObjectURL(prev);
      return URL.createObjectURL(file);
    });
  };

  // 컴포넌트 언마운트 시 마지막 URL 해제
  useEffect(() =&gt; {
    return () =&gt; {
      if (previewUrl) URL.revokeObjectURL(previewUrl);
    };
  }, [previewUrl]);

  return (
    &lt;&gt;
      &lt;input type=&quot;file&quot; accept=&quot;image/*&quot; onChange={handleChangeImage} /&gt;
      {previewUrl &amp;&amp; (
        &lt;img
          src={previewUrl}
          alt=&quot;preview&quot;
          // 이미 로딩이 끝났다면 바로 해제하는 패턴도 가능(선택)
          onLoad={() =&gt; {
            // URL.revokeObjectURL(previewUrl); // 선택사항
          }}
        /&gt;
      )}
    &lt;/&gt;
  );
}</code></pre>
<h4 id="filereaderreadasdataurl"><strong><code>FileReader.readAsDataURL</code></strong></h4>
<pre><code class="language-tsx">import { useState } from &quot;react&quot;;

export default function ImagePreviewBase64() {
  const [previewDataUrl, setPreviewDataUrl] = useState&lt;string | null&gt;(null);

  const handleChangeImage = (e: React.ChangeEvent&lt;HTMLInputElement&gt;) =&gt; {
    const file = e.target.files?.[0];
    if (!file) return;

    const reader = new FileReader(); //파일 리더 객체 지정
    reader.readAsDataURL(file);//파일 객체를 읽어서 이해 가능한 문자열로 변경
    reader.onload = () =&gt; {
      // onload 시점에만 result가 채워짐(비동기)
      setPreviewDataUrl(reader.result as string);
    };
  };

  return (
    &lt;&gt;
      &lt;input type=&quot;file&quot; accept=&quot;image/*&quot; onChange={handleChangeImage} /&gt;
      {previewDataUrl &amp;&amp; &lt;img src={previewDataUrl} alt=&quot;preview&quot; /&gt;}
    &lt;/&gt;
  );
}</code></pre>
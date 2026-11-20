# 인공지능 업스킬링 4주차 실습 가이드
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>교육 자료 · 4회차</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Nanum+Gothic:wght@400;700;800&family=Nanum+Gothic+Coding:wght@400;700&display=swap">
<style>
:root{
  --ground:#ffffff;
  --surface:#f6f8fb;
  --surface-2:#eceff4;
  --line:#dde1e8;
  --ink:#141c28;
  --ink-soft:#5c6675;
  --accent:#1b3252;
  --accent-deep:#0e1f38;
  --accent-soft:#e5eaf2;
  --mark-ink:#8a5206;
  --mark-bg:#fdf1dd;
  --mark-line:#e8c691;
  --ok:#1a6b48;
  --radius:14px;
  --step:1;
}
@media (prefers-color-scheme: dark){
  :root:not([data-theme="light"]){
    --ground:#12161d;--surface:#1a2029;--surface-2:#222a35;--line:#333d4b;
    --ink:#e8ecf2;--ink-soft:#a3aec0;--accent:#3d6aa3;--accent-deep:#5c8bc4;
    --accent-soft:#232f42;--mark-ink:#f2c684;--mark-bg:#3a2c14;--mark-line:#6b5124;--ok:#5cbd91;
  }
}
*{box-sizing:border-box}
body{
  margin:0;background:var(--ground);color:var(--ink);
  font-family:"Pretendard Variable","Pretendard","Nanum Gothic","Apple SD Gothic Neo","Malgun Gothic",sans-serif;
  font-size:calc(17px * var(--step));line-height:1.75;-webkit-text-size-adjust:100%;
}
.wrap{max-width:840px;margin:0 auto;padding:0 20px 80px}
.masthead{padding:44px 0 26px;border-bottom:2px solid var(--line)}
.eyebrow{font-size:.82em;font-weight:700;letter-spacing:.14em;color:var(--accent);margin:0 0 10px}
h1{font-size:2.1em;font-weight:800;line-height:1.25;margin:0 0 12px;letter-spacing:-.01em}
.lede{margin:0;color:var(--ink-soft);font-size:1.02em}
.lede strong{color:var(--ink)}
.toolbar{position:sticky;top:0;z-index:20;background:var(--ground);border-bottom:1px solid var(--line);padding:10px 0;margin-bottom:8px}
.toolbar-inner{max-width:840px;margin:0 auto;padding:0 20px;display:flex;flex-wrap:nowrap;gap:10px;align-items:center}
.jump{display:flex;gap:6px;flex-wrap:nowrap;flex:1 1 0;min-width:0;overflow-x:auto;scrollbar-width:none}
.jump::-webkit-scrollbar{display:none}
.jump a{flex:0 0 auto;padding:7px 13px;border-radius:999px;background:var(--surface);color:var(--ink-soft);text-decoration:none;font-size:.86em;font-weight:700;border:1px solid transparent;white-space:nowrap}
.jump a:hover,.jump a:focus-visible{background:var(--accent-soft);color:var(--accent-deep);border-color:var(--accent)}
.sizer{display:flex;align-items:center;gap:7px;flex:0 0 auto}
.sizer span{font-size:.82em;color:var(--ink-soft);font-weight:700}
.sizer button{width:38px;height:38px;border-radius:9px;border:1px solid var(--line);background:var(--surface);color:var(--ink);font-family:inherit;font-weight:800;cursor:pointer;font-size:1em;line-height:1}
section{margin-top:52px;scroll-margin-top:76px}
.sec-head{display:flex;align-items:baseline;gap:12px;margin-bottom:6px}
.sec-num{font-family:"Nanum Gothic Coding",monospace;font-size:1.5em;font-weight:700;color:var(--accent)}
h2{font-size:1.5em;font-weight:800;margin:0;letter-spacing:-.01em}
.sec-note{margin:0 0 22px;color:var(--ink-soft)}
.sub{font-size:1.18em;font-weight:800;margin:34px 0 12px;color:var(--accent-deep)}
.card{background:var(--surface);border:1px solid var(--line);border-radius:var(--radius);padding:22px 22px 20px;margin-bottom:18px}
.card h3{font-size:1.14em;font-weight:800;margin:0 0 8px}
.card p{margin:0 0 14px;color:var(--ink-soft)}
.card strong{color:var(--ink)}
pre{
  margin:0 0 14px;background:#1a2029 !important;color:#e8ecf2 !important;
  border:1px solid #333d4b;border-radius:10px;padding:18px;
  font-family:"Nanum Gothic Coding","D2Coding",monospace;font-size:.98em;line-height:1.85;
  white-space:pre-wrap;word-break:break-word;overflow-x:auto;
}
pre.long{max-height:22em;overflow-y:auto}
.ph{color:var(--mark-ink);font-weight:700;background:var(--mark-bg);box-shadow:inset 0 0 0 1px var(--mark-line);border-radius:4px;padding:1px 4px}
pre .ph{color:#f2c684;background:#3a2c14;box-shadow:inset 0 0 0 1px #6b5124}
button.copy{display:flex;align-items:center;justify-content:center;gap:9px;width:100%;min-height:58px;border:none;border-radius:10px;background:var(--accent);color:#fff;font-family:inherit;font-size:1.05em;font-weight:800;cursor:pointer}
button.copy:hover{background:var(--accent-deep)}
button.copy.done{background:var(--ok)}
button.copy .ico{font-family:"Nanum Gothic Coding",monospace;font-weight:700}
.chips{display:grid;gap:10px}
@media(min-width:620px){.chips{grid-template-columns:1fr 1fr}}
.chips.one{grid-template-columns:1fr}
button.chip{display:flex;align-items:center;justify-content:space-between;gap:10px;min-height:56px;padding:12px 16px;border:1px solid var(--line);border-radius:10px;background:var(--ground);color:var(--ink);font-family:"Nanum Gothic Coding",monospace;font-size:.96em;font-weight:700;text-align:left;cursor:pointer}
button.chip:hover{border-color:var(--accent);background:var(--accent-soft)}
button.chip.done{background:var(--ok);color:#fff;border-color:var(--ok)}
button.chip .tag{font-family:inherit;font-size:.82em;font-weight:700;opacity:.65;flex:0 0 auto}
.note{display:flex;gap:11px;background:var(--surface-2);border-radius:10px;padding:13px 15px;font-size:.94em;color:var(--ink-soft);margin-top:14px}
.note b{flex:0 0 auto;font-weight:800;color:var(--accent-deep)}
.note p{margin:0;color:inherit}
ol.steps{margin:0;padding:0;list-style:none;counter-reset:s}
ol.steps li{counter-increment:s;display:flex;gap:14px;align-items:flex-start;padding:11px 0;border-bottom:1px solid var(--line)}
ol.steps li:last-child{border-bottom:none}
ol.steps li::before{content:counter(s);flex:0 0 auto;width:30px;height:30px;border-radius:50%;background:var(--accent);color:#fff;font-family:"Nanum Gothic Coding",monospace;font-weight:700;display:flex;align-items:center;justify-content:center;font-size:.9em;margin-top:2px}
ol.steps b{font-weight:800}
.mlabel{display:block;font-weight:800;font-size:.9em;color:var(--accent-deep);margin:0 0 6px}
details.more{margin-top:16px;background:var(--ground);border:1px solid var(--line);border-radius:10px;overflow:hidden}
details.more summary{padding:15px 18px;font-weight:800;cursor:pointer;list-style:none;display:flex;justify-content:space-between;align-items:center}
details.more summary::-webkit-details-marker{display:none}
details.more summary::after{content:'＋';font-weight:800;color:var(--accent)}
details.more[open] summary{border-bottom:1px solid var(--line)}
details.more[open] summary::after{content:'－'}
.more-body{padding:16px 18px 18px}
.linkbtn{display:flex;align-items:center;justify-content:center;min-height:58px;border-radius:10px;margin:0 0 16px;background:var(--accent);color:#fff;font-weight:800;font-size:1.05em;text-decoration:none;text-align:center;padding:8px 14px}
.linkbtn:hover{background:var(--accent-deep)}
.banner{display:flex;flex-wrap:wrap;gap:8px 16px;align-items:center;background:var(--surface-2);border-radius:var(--radius);padding:16px 20px;margin-top:24px}
.banner .label{font-weight:800;font-size:.9em;color:var(--accent-deep)}
.banner .addr{font-family:"Nanum Gothic Coding",monospace;font-weight:700;font-size:1.08em}
.tbl{width:100%;border-collapse:collapse;font-size:.95em;background:var(--ground);border-radius:10px;overflow:hidden}
.tbl th,.tbl td{border-bottom:1px solid var(--line);padding:10px 12px;text-align:left;vertical-align:top}
.tbl th{background:var(--accent-soft);color:var(--accent-deep);font-weight:800}
.tbl tr:last-child td{border-bottom:none}
.tbl td:first-child{font-weight:800;white-space:nowrap}
.tbl-wrap{overflow-x:auto;border:1px solid var(--line);border-radius:10px}
ul.check{list-style:none;margin:0;padding:0}
ul.check li{display:flex;gap:12px;align-items:flex-start;padding:10px 0;border-bottom:1px solid var(--line)}
ul.check li:last-child{border-bottom:none}
ul.check input{width:22px;height:22px;margin-top:4px;flex:0 0 auto;accent-color:var(--ok)}
ul.check label{cursor:pointer}
.qr-row{display:flex;flex-wrap:wrap;gap:10px}
.qr-row input{flex:1 1 240px;min-height:52px;padding:12px;border:1px solid var(--line);border-radius:10px;background:var(--ground);color:var(--ink);font-family:inherit;font-size:1em}
.qr-row button{min-height:52px;padding:0 20px;border:none;border-radius:10px;background:var(--accent);color:#fff;font-family:inherit;font-weight:800;font-size:1em;cursor:pointer}
#qrcode{margin-top:18px}
#qrcode img,#qrcode canvas{background:#fff;padding:10px;border-radius:8px}
footer{margin-top:60px;padding-top:22px;border-top:1px solid var(--line);color:var(--ink-soft);font-size:.9em}
@media (prefers-reduced-motion: no-preference){
  button.copy,button.chip{transition:background .15s ease,border-color .15s ease}
}
.flow{display:flex;flex-wrap:wrap;gap:6px;margin:0 0 18px;padding:0;list-style:none}
.flow li{padding:6px 12px;border-radius:999px;background:var(--surface-2);color:var(--ink-soft);font-weight:800;font-size:.86em}
.flow li.on{background:var(--accent);color:#fff}
.answer{display:flex;gap:11px;background:var(--mark-bg);border:1px solid var(--mark-line);border-radius:10px;padding:13px 15px;font-size:.94em;margin-top:14px}
.answer b{flex:0 0 auto;font-weight:800;color:var(--mark-ink)}
.answer p{margin:0;color:var(--ink)}
.answer strong{color:var(--mark-ink)}
</style>
</head>
<body>
<div class="toolbar">
  <div class="toolbar-inner">
    <nav class="jump" aria-label="바로가기">
      <a href="#s0">0 시작하기</a>
      <a href="#s1">1 AI 환경 세팅</a>
      <a href="#s2">2 요약·번역</a>
      <a href="#s3">3 짧은 글쓰기</a>
      <a href="#check">✓ 마무리</a>
    </nav>
    <div class="sizer">
      <span>글자</span>
      <button type="button" id="smaller" aria-label="글자 작게">－</button>
      <button type="button" id="bigger" aria-label="글자 크게">＋</button>
    </div>
  </div>
</div>
<div class="wrap">
<header class="masthead">
  <p class="eyebrow">교육 프로그램 · 4회차</p>
  <h1>AI와 일상, AI와 업무</h1>
  <p class="lede">오늘 쓸 프롬프트가 순서대로 담겨 있습니다. <strong>복사하기 버튼</strong>을 누르면 문장이 복사되고, <span class="ph">[노란 칸]</span>만 내 이야기로 바꾸면 됩니다.</p>
</header>

<!-- ───────────── 0. 시작하기 ───────────── -->
<section id="s0">
  <div class="sec-head"><span class="sec-num">0</span><h2>시작하기</h2></div>
  <p class="sec-note">프롬프트 쓰는 방법과 오늘 수업의 순서입니다.</p>
  <div class="card">
    <h3>프롬프트 쓰는 순서</h3>
    <ol class="steps">
      <li><span><b>복사하기</b> 버튼을 누릅니다.</span></li>
      <li><span>AI 대화창(Gemini)을 누르고 <b>Ctrl + V</b>로 붙여넣습니다.</span></li>
      <li><span><b>[대괄호]</b> 안의 글자를 지우고 내 내용을 씁니다. 대괄호 기호도 함께 지웁니다.</span></li>
      <li><span><b>엔터</b>를 누르고 AI의 답을 기다립니다.</span></li>
    </ol>
    <div class="note"><b>TIP</b><p>타자가 힘들 때는 대화창의 마이크 모양 버튼을 눌러 말로 입력해 보세요.</p></div>
  </div>
  <div class="card">
    <h3>오늘의 순서</h3>
    <p>남은 3주(4~6주차)는 <strong>내 일에 적용하기</strong>입니다. 자료 정리 · 문서 작성 · 데이터 분석 · 마무리 프로젝트. 오늘은 그 네 번째 시간입니다.</p>
    <ol class="steps">
      <li><span><b>'나'를 위한 AI 환경 세팅하기</b> — 나만의 AI 환경 구성하기</span></li>
      <li><span><b>요약/번역하기 + 논문 읽기</b> — AI로 요약하고 번역하기</span></li>
      <li><span><b>짧은 글쓰기</b> — 인사말 · 모임 안내 문구 만들기</span></li>
    </ol>
    <details class="more">
      <summary>지난 3주, 이것을 배웠습니다</summary>
      <div class="more-body">
        <div class="tbl-wrap">
          <table class="tbl">
            <tr><th>주차</th><th>핵심</th><th>해 본 것</th></tr>
            <tr><td>1주 · 글과 그림</td><td>조건을 적으면 결과가 달라집니다</td><td>역할·맥락·형식·예시 · 나만의 캐릭터 · 소개 영상(Vrew)</td></tr>
            <tr><td>2주 · AI 비서</td><td>한 번 알려 주면 기억합니다</td><td>사진 보여 주고 묻기 · 요리 비서(스킬) · AI 에이전트</td></tr>
            <tr><td>3주 · 노래와 앱</td><td>말로 주고받으며 고쳐 갑니다</td><td>응원가(수노) · 디지털 명함 · 말로 만든 앱(Canvas)</td></tr>
          </table>
        </div>
        <div class="note"><b>기억하기</b><p>원하는 것을 정확히 말하기</p></div>
      </div>
    </details>
  </div>
</section>

<!-- ───────────── 1. AI 환경 세팅 ───────────── -->
<section id="s1">
  <div class="sec-head"><span class="sec-num">1</span><h2>'나'를 위한 AI 환경 세팅하기</h2></div>
  <p class="sec-note">한 번 알려 두면 AI가 매번 내 방식대로 답합니다. 나만의 AI 환경을 구성해 봅니다.</p>
  <div class="card">
    <h3>구글 워크스페이스(Google Workspace)란?</h3>
    <p>구글이 제공하는 클라우드 기반의 업무용 생산성·협업 도구 모음입니다. <strong>Gmail, 구글 드라이브, 구글 문서, 시트, 슬라이드, 캘린더</strong> 등이 들어 있습니다.</p>
  </div>

  <h3 class="sub">'나'를 위한 Gemini 만들기</h3>
  <div class="card">
    <h3>Gemini 개인 환경 구성하기</h3>
    <ol class="steps">
      <li><span><b>gemini.google.com</b>에 접속합니다.</span></li>
      <li><span><b>설정 → 개인 인텔리전스</b>로 들어갑니다.</span></li>
      <li><span><b>메모리</b>를 켜면 Gemini가 이전 대화를 바탕으로 나를 기억합니다. 기억한 내용은 직접 보고 삭제할 수 있습니다.</span></li>
      <li><span><b>연결된 앱</b>에서 Gmail · 캘린더 같은 구글 앱을 연결할 수 있습니다.</span></li>
      <li><span><b>Gemini 요청 사항</b>을 누르고 아래 내용을 붙여넣은 뒤 저장합니다.</span></li>
    </ol>
  </div>
  <div class="card">
    <h3>Gemini 요청 사항 칸</h3>
    <pre data-copy>[답변 기본 원칙]
요약으로 대답 시작 (가장 중요한 결론 1~2줄 먼저 제시)
긴 단락에 글머리 기호(•) 사용
구체적인 예시 제시 (상황·대화·실제 사례 활용)
한 문장은 짧고 간결하게 작성
굵은 글씨(강조)를 활용해 핵심 단어 표시

[설명 방식 및 어조]
전문 용어나 외래어 대신 쉬운 우리말로 풀어서 설명
영어·전문 용어 사용 시 괄호 안에 뜻 풀이 병기
다정하고 예의 바른 존댓말 사용

[실생활 활용 맞춤]
방법 안내 시 1, 2, 3 순서대로 단계별 설명
건강·금융·제도 관련 질문 시 주의사항이나 확인해야 할 점 함께 안내
답변 마지막에 추가로 물어볼 만한 연관 질문 1~2가지 제안</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
    <div class="note"><b>기억하기</b><p>요청 사항은 한 번 저장하면 모든 대화에 적용됩니다. 내 마음에 맞게 줄을 더하거나 빼도 좋습니다.</p></div>
  </div>

  <details class="more">
    <summary>(선택) ChatGPT 사용자 지정 지침</summary>
    <div class="more-body">
      <div class="card">
        <ol class="steps">
          <li><span>ChatGPT <b>설정 → 개인 맞춤 설정</b>으로 들어갑니다.</span></li>
          <li><span><b>사용자 지정 지침</b>의 <b>편집(Edit)</b>을 누릅니다.</span></li>
          <li><span>아래 내용을 붙여넣고 <b>저장</b>합니다.</span></li>
        </ol>
      </div>
      <div class="card">
        <pre data-copy>답변을 짧게 해줘.
중요한 내용부터 알려줘.
어려운 말은 쉬운 말로 바꿔줘.
한국어로 친절하게 존댓말을 써줘.
사용 방법은 한 단계씩 번호를 붙여 알려줘.
잘 모르겠으면 무엇을 확인해야 하는지 알려줘.</pre>
        <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
      </div>
    </div>
  </details>

  <details class="more">
    <summary>(선택) Claude 지침</summary>
    <div class="more-body">
      <div class="card">
        <ol class="steps">
          <li><span>Claude 왼쪽 아래 <b>내 이름</b>을 누르고 <b>설정</b>으로 들어갑니다.</span></li>
          <li><span><b>일반</b> 메뉴의 <b>지침</b> 칸에 아래 내용을 붙여넣습니다.</span></li>
        </ol>
      </div>
      <div class="card">
        <pre data-copy class="long">1. 말투와 설명 방식
- 존댓말을 쓰되 지나치게 딱딱하지 않게, 친절한 상담원처럼 설명할 것
- 전문 용어와 영어 약어는 되도록 쓰지 말고, 꼭 써야 하면 괄호 안에 쉬운 말로 풀어 줄 것 (예: 앱(스마트폰 프로그램))
- 한 번에 너무 많은 정보를 주지 말고, 핵심부터 3~5줄 이내로 먼저 답할 것
- 더 알고 싶으면 이어서 물어보라고 마지막에 한 줄 덧붙일 것

2. 일상생활 도움
- 문자나 카톡 답장, 경조사 인사말, 단체방 공지 같은 글은 바로 보낼 수 있는 완성된 문장으로 써 줄 것
- 같은 내용이라도 격식 있는 말투와 편한 말투로 두 가지를 보여 줄 것
- 요리법, 여행 일정, 장보기 목록은 표나 목록으로 간단히 정리해 줄 것

3. 확인과 정확성
- 질문이 애매하면 짐작해서 답하지 말고 한 가지만 다시 물어볼 것
- 확실하지 않은 내용은 "확실하지 않다"고 분명히 말할 것
- 날짜, 금액, 전화번호처럼 중요한 정보는 한 번 더 강조해서 보여 줄 것</pre>
        <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
      </div>
    </div>
  </details>
</section>

<!-- ───────────── 2. 요약 · 번역 ───────────── -->
<section id="s2">
  <div class="sec-head"><span class="sec-num">2</span><h2>요약/번역하기 + 논문 읽기</h2></div>
  <p class="sec-note">AI로 글과 영상을 요약하고, 다른 나라 말로 번역하고, 논문도 읽어 봅니다.</p>

  <h3 class="sub">요약하기</h3>
  <div class="card">
    <p>긴 문서나 여러 자료에서 핵심만 뽑아 간단하게 보여 줍니다. 표, 목록, 한 단락 요약처럼 <strong>형식을 정해 줄 수도</strong> 있습니다. (예: 정책 보고서 핵심 3줄 요약, 두 행사 내용 비교표)</p>
  </div>
  <div class="card">
    <h3>글 요약하기</h3>
    <ol class="steps">
      <li><span>구글에서 <b>AI 업무</b>를 검색합니다.</span></li>
      <li><span>잡코리아 <b>'현직 개발자들이 만든 진짜 AI 업무 자동화 사례'</b> 글을 엽니다.</span></li>
      <li><span>아래 프롬프트를 붙여넣고 보냅니다.</span></li>
    </ol>
    <pre data-copy>https://www.jobkorea.co.kr/recruit/careers/articles/internal-ai-automation-cases
위의 글 요약해줘</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
    <span class="mlabel" style="margin-top:16px">더 물어보기</span>
    <div class="chips">
      <button class="chip" type="button" data-copy="핵심만 3줄로 다시 요약해줘">핵심만 3줄로 다시 요약해줘<span class="tag">복사</span></button>
      <button class="chip" type="button" data-copy="표로 정리해줘">표로 정리해줘<span class="tag">복사</span></button>
    </div>
  </div>
  <div class="card">
    <h3>유튜브 영상 요약하기</h3>
    <pre data-copy>https://www.youtube.com/watch?v=R-02LYDHnBo&amp;t=155s
이 영상을 요약해줘</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
    <div class="answer"><b>확인 포인트</b><p>요약 옆의 <strong>[25:50]</strong> 같은 시간 표시를 누르면 영상의 그 장면으로 갑니다. 정말 그렇게 말했는지 확인해 보세요.</p></div>
  </div>

  <h3 class="sub">번역하기</h3>
  <div class="card">
    <p>외국어 자료를 원하는 언어로 자연스럽게 바꿔 줍니다. 직역·의역을 고르고, <strong>말투와 분위기</strong>도 정할 수 있습니다. (예: 행사 홍보 문구를 영어로, 보도자료는 격식체 · SNS는 친근체)</p>
  </div>
  <div class="card">
    <h3>영어 시 번역하기</h3>
    <pre data-copy class="long">Leisure
By W. H. Davies

What is this life if, full of care,
We have no time to stand and stare?
No time to stand beneath the boughs
And stare as long as sheep or cows:
No time to see, when woods we pass,
Where squirrels hide their nuts in grass:
No time to see, in broad daylight,
Streams full of stars, like skies at night:
No time to turn at Beauty’s glance,
And watch her feet, how they can dance:
No time to wait till her mouth can
Enrich that smile her eyes began?
A poor life this if, full of care,
We have no time to stand and stare.

위 영어 시의 아름다운 운율과 서정적인 감성을 살려서, 한국 시(詩)처럼 여운이 남고 감성적인 문장으로 번역해 줘</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
  </div>
  <div class="card">
    <h3>한글 → 영어로 번역하기</h3>
    <pre data-copy>[오늘 날씨가 정말 좋네요! 좋은 하루 보내시고 주말에 뵙겠습니다.]
위 한국어 문장을 외국 친구에게 보내는 것처럼, 다정하고 친근한 일상 영어로 번역해 줘.</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
  </div>
  <div class="card">
    <h3>영어로 글쓰기 · 생일 축하 문자</h3>
    <pre data-copy>외국인 지인의 생일을 진심으로 축하해 주는 문자를 보낼 거야. 생일 진심으로 축하하고, 올해도 좋은 일만 가득하길 바란다는 말을 따뜻하고 다정한 감성으로 영어로 작성해 줘.</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
  </div>
  <div class="card">
    <h3>영어로 글쓰기 · 쇼핑몰 교환 문의</h3>
    <pre data-copy>외국 쇼핑몰 고객센터에 보낼 1:1 문의글이야. 물건이 파손되어 도착해서 교환을 받고 싶다는 내용을 명확하고 정중한 비즈니스 톤의 영어로 작성해 줘.</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
  </div>
  <div class="card">
    <h3>이 연설문, 누구의 연설문일까요?</h3>
    <p>아래 연설문을 복사해 붙여넣고, 끝에 <strong>"한국어로 번역해줘"</strong>를 덧붙여 보내 보세요.</p>
    <pre data-copy class="long">Thank you, Mr. Secretary General, UNICEF Executive Director, and all the excellencies and guests from all over the world. My name is Kim Nam-joon, also known as RM, the leader of the group BTS. It is an honor to be invited to an occasion of such significance for today's young generation.

Last November, BTS launched the 'Love Myself' campaign with UNICEF, building on our belief that 'true love first begins with loving myself.' We started to hear remarkable stories from our fans all over the world, how our message helped them overcome their hardships in life and start loving themselves. These stories constantly remind us of our responsibility.

So, let's take one more step. We have learned to love ourselves, so now I urge you to speak yourself. No matter who you are, where you're from, your skin color, your gender identity, speak yourself. Find your name, find your voice by speaking yourself.

I was born in Ilsan, a city near Seoul, Korea. It’s a truly beautiful place with a lake, hills, and even an autumn flower festival. I spent a very happy childhood there, and I was just an ordinary boy. I used to look up at the night sky in wonder and I used to dream the dreams of a boy.

However, I think that when I was about nine or ten, my heart stopped. Looking back, that's when I began to worry about what other people thought of me and started seeing myself through their eyes. I stopped looking up at the night sky. I stopped daydreaming. Instead, I tried to jam myself into the molds that other people made. Soon, I began to shut out my own voice and started to listen to the voices of others. No one called out my name, and neither did I. My heart stopped and my eyes closed.

And so, I, we, all lost our names. We became like ghosts. But I had one shelter, and that was music. There was a small voice inside of me that said, 'Wake up, man, and listen to yourself!' But it took a long time for me to hear music calling my true name.

Even after joining BTS, there were hurdles. People might not believe it, but sometimes, a lot of people thought we were hopeless. Sometimes I just wanted to quit. But I think I was very lucky that I didn't give all of this up. And I'm sure that I, and we, will keep stumbling and falling like this. BTS has become artists performing in huge stadiums and selling millions of albums, but I am still an ordinary 24-year-old man.

If there's anything I've achieved, it was only possible that I had my members right by me, and with the love and support of our 'ARMY' fans all over the world.

Today, I take all my faults and all my tracks, for who I am, with all my leashes and all my faults. And I'm going to love myself even more, for who I was, who I am, and who I will be.

What is your name? What excites you and makes your heart beat? Tell me your story. I want to hear your voice, and I want to hear your conviction. No matter who you are, where you're from, your skin color, your gender identity: speak yourself. Find your name, find your voice by speaking yourself. Thank you very much.</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
  </div>

  <h3 class="sub">논문 읽어보기 · 구글 스칼라</h3>
  <div class="card">
    <ol class="steps">
      <li><span><b>scholar.google.co.kr</b>(구글 학술검색)에 접속합니다.</span></li>
      <li><span>궁금한 주제를 검색하고, 오른쪽에 <b>[PDF]</b> 표시가 있는 논문을 내려받습니다.</span></li>
      <li><span>Gemini 대화창 왼쪽 <b>＋</b>를 눌러 PDF를 올리고 아래 프롬프트를 보냅니다.</span></li>
    </ol>
    <pre data-copy>올린 논문을 처음 읽는 사람도 이해할 수 있게 쉬운 말로 설명해줘.
- 무엇을 알아보려고 했는지
- 어떻게 조사했는지
- 무엇을 알아냈는지
각각 두 줄 이내로 정리해줘.</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
    <div class="note"><b>기억하기</b><p>AI 요약은 초안입니다. 중요한 숫자와 결론은 논문 원문에서 다시 확인하세요.</p></div>
  </div>
</section>

<!-- ───────────── 3. 짧은 글쓰기 ───────────── -->
<section id="s3">
  <div class="sec-head"><span class="sec-num">3</span><h2>짧은 글쓰기</h2></div>
  <p class="sec-note">인사말과 모임 안내 문구를 만들고, 인사말을 카드 이미지로도 만들어 봅니다.</p>

  <h3 class="sub">모임 안내</h3>
  <div class="card">
    <h3>동창회 안내 문자 쓰기</h3>
    <pre data-copy>다음 내용을 바탕으로 친구들에게 보낼 친근한 [동창회 안내 문자]를 만들어줘.

모임 이름: [시대고등학교 27회 졸업생] 모임
날짜 및 시간: [10월 5일 토요일 오후 6시]
장소: [서울역 앞 OO고깃집]
분위기: [오랜만에 만나는 거라 반갑고 편안한 느낌으로 이모티콘 곁들여서] 작성해 줘.</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
  </div>
  <div class="card">
    <h3>모임 참여 독려하기</h3>
    <pre data-copy>모임 날짜를 며칠 앞두고, 아직 참석 여부를 알려주지 않은 분들에게 보낼 리마인드(독려) 문자를 작성해줘.

대상: [산악 동호회 모임 회원들]
분위기: [재촉하거나 부담 주는 느낌 없이, 따뜻하고 정중하게 안부를 물으며 인원을 확정해야 한다는 점을 알리는 느낌]
모임정보: [10월 5일 토요일 저녁 7시] / [강남역] / [다음주 수요일까지] 회신
포함할 내용: 식당 예약과 준비 때문에 인원 확정이 필요하다는 점을 부드럽게 전하고, 바쁘겠지만 참석 여부를 꼭 회신해 달라는 당부의 멘트</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
  </div>

  <h3 class="sub">연말 인사</h3>
  <div class="card">
    <h3>친구에게 보내는 연말 인사말</h3>
    <pre data-copy>소중한 친구에게 카카오톡으로 보낼 연말 인사말을 만들어줘.
대상 · [30대 친구]
분위기 · [정겹고 따뜻하며 부담 없는 느낌] (이모지 1~2개 포함)
내용 · 올해 함께한 시간이 즐거웠다는 말, 늘 곁에 있어줘서 고맙다는 마음, 남은 한 해도 건강하고 따뜻하게 보내라는 인사 포함
길이 · 3문장 정도</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
    <span class="mlabel" style="margin-top:16px">더 물어보기</span>
    <div class="chips">
      <button class="chip" type="button" data-copy="조금 더 짧게 줄여줘">조금 더 짧게 줄여줘<span class="tag">복사</span></button>
      <button class="chip" type="button" data-copy="격식 있는 말투로도 하나 써줘">격식 있는 말투로도 하나 써줘<span class="tag">복사</span></button>
    </div>
  </div>
  <div class="card">
    <h3>송년 모임 안내 문구</h3>
    <pre data-copy>친구들 단체 카카오톡방에 올릴 송년 모임 안내 문구를 만들어줘.
대상 · [30대 친구 모임]
분위기 · [반갑고 편안한 느낌] (이모지 1~2개 포함)
내용 · 올해가 가기 전에 함께 저녁을 먹자는 말, 모임 일시와 장소, 참석 여부를 알려 달라는 말 포함
모임 정보 · [12월 12일 토요일 저녁 6시] / [시청역 근처 식당 '만족오향족발']
회신 방법 · [12월 5일까지] 단체 카카오톡방에 참석 여부 남기기
형식 · 일시와 장소는 줄을 나눠 한눈에 보이게 작성</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
  </div>

  <h3 class="sub">인사말을 카드 이미지로</h3>
  <div class="card">
    <h3>연말 카드 만들기</h3>
    <pre data-copy>아래 인사말을 넣어서, 눈이 소복이 내리고 창문마다 따뜻한 불빛이 비치는 골목을 배경으로 연말 카드를 만들어줘. 오랜 친구에게 보내는 카드처럼 정겹고 포근한 느낌이면 좋겠어. 글씨는 배경과 겹치지 않게 배치하고 크게 써줘.
"[올 한 해 함께해 줘서 고마워. 남은 연말도 따뜻하게 보내!]"</pre>
    <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
  </div>
  <details class="more">
    <summary>크리스마스 · 새해 카드도 만들어 보기 (선택)</summary>
    <div class="more-body">
      <div class="card">
        <h3>크리스마스 카드</h3>
        <pre data-copy>아래 인사말을 넣어서, 반짝이는 크리스마스트리와 벽난로가 있는 거실을 배경으로 크리스마스 카드를 만들어줘. 따뜻한 조명과 빨간색 장식이 어우러지게 하고, 카카오톡에서 보기 좋은 정사각형 이미지로 만들어줘.
"[메리 크리스마스! 웃음 가득한 하루 보내!]"</pre>
        <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
      </div>
      <div class="card">
        <h3>새해 카드</h3>
        <pre data-copy>아래 인사말을 넣어서, 잔잔한 바다 위로 새해 첫 해가 떠오르는 풍경을 배경으로 새해 카드를 만들어줘. 하늘은 붉은빛과 금빛이 어우러지게 하고, 인사말은 하늘의 여백에 크고 또렷하게 써줘.
"[2027년 새해 복 많이 받으세요. 건강하고 좋은 일 가득한 한 해 되세요!]"</pre>
        <button class="copy" type="button"><span class="ico">⧉</span>복사하기</button>
      </div>
      <div class="note"><b>기억하기</b><p>그림 속 글자가 깨지면 "글자는 빼고 그려줘"라고 한 뒤, 인사말은 문자로 함께 보내세요.</p></div>
    </div>
  </details>
</section>

<!-- ───────────── 마무리 ───────────── -->
<section id="check">
  <div class="sec-head"><span class="sec-num">✓</span><h2>마무리</h2></div>
  <p class="sec-note">다음 시간 미리 보기와 꼭 지킬 것입니다.</p>
  <div class="card">
    <h3>다음 시간에는</h3>
    <ol class="steps">
      <li><span>긴 글쓰기 / 퇴고하기</span></li>
      <li><span>데이터 분석하기</span></li>
      <li><span>문서 만들기</span></li>
    </ol>
    <div class="note"><b>다음 수업</b><p><strong>12.05.(토)</strong> · <strong>12.12.(토)</strong> 꼭 기억해 주세요!</p></div>
  </div>
  <div class="card">
    <ul class="check">
      <li><input type="checkbox" id="c1"><label for="c1">Gemini 요청 사항을 저장했다.</label></li>
      <li><input type="checkbox" id="c2"><label for="c2">AI 요약에서 중요한 숫자와 결론은 원문에서 다시 확인했다.</label></li>
      <li><input type="checkbox" id="c3"><label for="c3">만든 인사말이나 카드를 결과물 올리는 곳에 올렸다.</label></li>
      <li><input type="checkbox" id="c4"><label for="c4">수업이 끝난 뒤 오른쪽 위 내 사진 → '로그아웃'을 눌렀다.</label></li>
    </ul>
  </div>
</section>
<div class="banner">
  <span class="label">결과물 올리는 곳</span>
  <span class="addr">bit.ly/업스킬링</span>
</div>
<div class="card" style="margin-top:24px">
  <h3>QR코드 만들기</h3>
  <p>만든 카드 이미지나 대화 공유 주소를 넣으면 QR코드가 만들어집니다.</p>
  <div class="qr-row">
    <input type="text" id="qr-link" placeholder="https://example.com" aria-label="QR코드로 만들 주소">
    <button type="button" id="qr-make">QR코드 만들기</button>
  </div>
  <div id="qrcode"></div>
</div>
<footer>
  <p><b>마치기 전에 꼭</b> — 공용 컴퓨터라 로그아웃을 안 하시면 다음 사람이 내 계정을 볼 수 있습니다. ① 오른쪽 위 내 사진 클릭 ② '로그아웃' 클릭</p>
  <p>감사합니다. 문의: cwh525@uos.ac.kr</p>
</footer>
</div>
<script src="https://cdn.jsdelivr.net/npm/qrcodejs@1.0.0/qrcode.min.js"></script>
<script>
(function(){
  /* [대괄호] 부분 노란색 표시 (복사되는 문장은 그대로) */
  var KEEP=['[답변 기본 원칙]','[설명 방식 및 어조]','[실생활 활용 맞춤]','[PDF]'];
  document.querySelectorAll('pre[data-copy]').forEach(function(pre){
    var raw = pre.textContent;
    pre.setAttribute('data-copy', raw);
    var html = raw
      .replace(/&/g,'&amp;')
      .replace(/</g,'&lt;')
      .replace(/>/g,'&gt;')
      .replace(/\[[^\]\n]*\]/g,function(m){
        if(KEEP.indexOf(m)>-1) return m;
        return '<span class="ph">' + m + '</span>';
      });
    pre.innerHTML = html;
  });
  /* 복사 기능 */
  function legacy(text){
    var ta = document.createElement('textarea');
    ta.value = text;
    ta.setAttribute('readonly','');
    ta.style.position = 'fixed';
    ta.style.top = '0';
    ta.style.opacity = '0';
    document.body.appendChild(ta);
    ta.select();
    var ok = false;
    try{ok=document.execCommand('copy')}catch(e){ok=false}
    document.body.removeChild(ta);
    return ok;
  }
  function copyText(text){
    if(navigator.clipboard && window.isSecureContext){
      return navigator.clipboard.writeText(text).then(
        function(){return true},
        function(){return legacy(text)}
      );
    }
    return Promise.resolve(legacy(text));
  }
  function flash(btn,label){
    var original=btn.dataset.label||btn.innerHTML;
    btn.dataset.label=original;
    btn.classList.add('done');
    btn.innerHTML=label;
    clearTimeout(btn._t);
    btn._t=setTimeout(function(){
      btn.classList.remove('done');
      btn.innerHTML=btn.dataset.label;
    },1800);
  }
  document.querySelectorAll('button.copy').forEach(function(btn){
    btn.addEventListener('click',function(){
      var pre=btn.parentElement.querySelector('pre[data-copy]');
      if(!pre) return;
      copyText(pre.getAttribute('data-copy')).then(function(ok){
        flash(btn,ok?'복사됐습니다':'복사가 안 됩니다');
      });
    });
  });
  document.querySelectorAll('button.chip').forEach(function(btn){
    btn.addEventListener('click',function(){
      copyText(btn.getAttribute('data-copy')).then(function(ok){
        flash(btn,ok?'복사됐습니다':'복사가 안 됩니다');
      });
    });
  });
  /* 글자 크기 */
  var STEPS=[1,1.15,1.32,1.5];
  var idx=0;
  try{
    var saved=localStorage.getItem('uskill-size');
    if(saved!==null) idx=Math.min(STEPS.length-1,Math.max(0,parseInt(saved,10)||0));
  }catch(e){}
  function apply(){
    document.documentElement.style.setProperty('--step',STEPS[idx]);
    try{localStorage.setItem('uskill-size',String(idx))}catch(e){}
  }
  apply();
  document.getElementById('bigger').addEventListener('click',function(){
    if(idx<STEPS.length-1){idx++;apply()}
  });
  document.getElementById('smaller').addEventListener('click',function(){
    if(idx>0){idx--;apply()}
  });
  /* QR코드 */
  document.getElementById('qr-make').addEventListener('click',function(){
    var link=document.getElementById('qr-link').value.trim();
    var box=document.getElementById('qrcode');
    if(!link){alert('링크를 입력해주세요.');return;}
    box.innerHTML='';
    if(typeof QRCode==='undefined'){box.textContent='QR코드 도구를 불러오지 못했습니다.';return;}
    new QRCode(box,{text:link,width:200,height:200});
  });
})();
</script>
</body>
</html>

---
marp: true
theme: default
paginate: false
style: |
  section {
    font-family: 'Helvetica Neue', sans-serif;
    padding: 40px 60px;
    box-sizing: border-box;
    overflow: hidden;
  }
  h1 {
    font-size: 1.4rem;
    color: #1a1a2e;
    border-bottom: 3px solid #1a1a2e;
    padding-bottom: 10px;
    margin: 0 0 16px 0;
    white-space: nowrap;
  }
  ul, ol { margin: 0; padding-left: 1.4em; }
  li { margin-bottom: 8px; font-size: 0.85rem; }
  pre {
    padding: 10px 14px;
    border-radius: 6px;
    background: #f4f4f4;
    overflow: hidden;
    max-height: 180px;
  }
  code { background: #eee; padding: 2px 6px; border-radius: 4px; font-family: monospace; }
  strong { color: #1a1a2e; }
  blockquote { background: #f5f7ff; border-left: 4px solid #1a1a2e; padding: 8px 14px; border-radius: 4px; margin: 12px 0; font-size: 0.85rem; }
  .before { background: #fff3f3; border-left: 4px solid #e74c3c; padding: 8px 14px; border-radius: 4px; margin-bottom: 10px; }
  .after  { background: #f0fff4; border-left: 4px solid #27ae60; padding: 8px 14px; border-radius: 4px; }

  /* 表紙用 */
  section.cover {
    background: #1a1a2e;
    color: #ffffff;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
  }
  section.cover .label {
    font-size: 0.75rem;
    letter-spacing: 0.15em;
    color: #7ecfff;
    text-transform: uppercase;
    margin-bottom: 12px;
  }
  section.cover .title-main {
    font-size: 2.2rem;
    font-weight: 700;
    color: #ffffff;
    line-height: 1.2;
    margin-bottom: 16px;
  }
  section.cover .title-sub {
    font-size: 1.0rem;
    color: #aac8e8;
    margin-bottom: 32px;
    line-height: 1.6;
  }
  section.cover .divider {
    width: 60px;
    height: 3px;
    background: #7ecfff;
    margin-bottom: 24px;
  }
  section.cover .profile {
    font-size: 0.72rem;
    color: #8aabbf;
    line-height: 1.8;
  }

  /* 本文スライド共通 */
  .highlight-box {
    background: #eef4ff;
    border-left: 4px solid #1a1a2e;
    padding: 10px 16px;
    border-radius: 4px;
    margin: 10px 0;
    font-size: 0.82rem;
    line-height: 1.6;
  }
  .pain-box {
    background: #fff7f0;
    border-left: 4px solid #e07820;
    padding: 10px 16px;
    border-radius: 4px;
    margin: 10px 0;
    font-size: 0.82rem;
    line-height: 1.6;
  }
  .skill-box {
    background: #f5f7ff;
    border: 1px solid #c8d4f8;
    border-radius: 8px;
    padding: 12px 18px;
    margin: 8px 0;
    font-size: 0.82rem;
    line-height: 1.6;
  }
  .skill-label {
    font-size: 0.65rem;
    letter-spacing: 0.1em;
    color: #7ecfff;
    background: #1a1a2e;
    display: inline-block;
    padding: 2px 8px;
    border-radius: 3px;
    margin-bottom: 4px;
  }

  /* スライド2 カードグリッド */
  .card-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 1fr 1fr;
    gap: 16px;
    margin-top: 8px;
    height: 330px;
  }
  .card {
    background: #ffffff;
    border-radius: 12px;
    padding: 18px 22px;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    gap: 8px;
    box-shadow: 0 2px 12px rgba(26,26,46,0.08);
    border-top: 3px solid #1a1a2e;
    position: relative;
  }
  .card-num {
    position: absolute;
    top: -1px;
    right: 18px;
    background: #1a1a2e;
    color: #ffffff;
    font-size: 0.6rem;
    font-weight: 700;
    letter-spacing: 0.12em;
    padding: 3px 10px;
    border-radius: 0 0 6px 6px;
  }
  .card-tag {
    font-size: 0.62rem;
    font-weight: 700;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: #888;
    margin-bottom: 0;
  }
  .card-text {
    font-size: 0.84rem;
    line-height: 1.65;
    color: #1a1a2e;
    margin: 0;
    font-weight: 400;
  }

  /* ポイントスライド */
  .point-list {
    display: flex;
    flex-direction: column;
    gap: 20px;
    margin-top: 8px;
  }
  .point-item {
    display: flex;
    align-items: flex-start;
    gap: 20px;
    background: #fff;
    border-radius: 12px;
    padding: 20px 24px;
    box-shadow: 0 2px 12px rgba(26,26,46,0.07);
  }
  .point-num {
    font-size: 2rem;
    font-weight: 800;
    color: #e8eaf0;
    line-height: 1;
    min-width: 36px;
    letter-spacing: -2px;
  }
  .point-body {}
  .point-title {
    font-size: 0.9rem;
    font-weight: 700;
    color: #1a1a2e;
    margin: 0 0 4px 0;
    border-left: 3px solid #1a1a2e;
    padding-left: 10px;
  }
  .point-desc {
    font-size: 0.78rem;
    color: #555;
    line-height: 1.65;
    margin: 0;
    padding-left: 13px;
  }

  /* メッセージスライド */
  section.message {
    background: #f9f9fb;
  }
  .msg-quote {
    font-size: 3.5rem;
    line-height: 1;
    color: #e0e2ea;
    font-family: Georgia, serif;
    margin-bottom: -10px;
  }
  .msg-body {
    font-size: 0.86rem;
    color: #555;
    line-height: 2.0;
    margin: 0 0 20px 0;
  }
  .msg-highlight {
    display: block;
    background: #fff;
    border-left: 3px solid #1a1a2e;
    padding: 14px 22px;
    border-radius: 0 12px 12px 0;
    font-size: 1.0rem;
    font-weight: 700;
    color: #1a1a2e;
    line-height: 1.8;
    margin-bottom: 20px;
    box-shadow: 0 2px 12px rgba(26,26,46,0.07);
  }
  .msg-footer {
    font-size: 0.7rem;
    color: #aaa;
    border-top: 1px solid #e0e2ea;
    padding-top: 14px;
    width: 100%;
  }
---

<!-- _class: cover -->

<div class="label">AGI-Lab × AIエージェントハッカソン</div>
<div class="title-main">Handson Hub Agent</div>
<div class="title-sub">AIハンズオン開催アシスタント<br>〜 最新機能の調査から当日資料まで、一気通貫 〜</div>
<div class="divider"></div>
<div class="profile">
通信会社 生成AI活用・DX推進担当<br>
伊藤 カイ
</div>

---

# ハッカソンテーマ：エバンジェリストを増やすには？

<div class="card-grid">

<div class="card">
<span class="card-num">背景</span>
<span class="card-tag">BACKGROUND</span>
<p class="card-text">AIの新機能・事例が次々登場。<br>情報は十分すぎるくらいある時代。</p>
</div>

<div class="card">
<span class="card-num">ターゲット</span>
<span class="card-tag">TARGET</span>
<p class="card-text">社内でAI活用の Hub になりたい<br>DX 推進担当者</p>
</div>

<div class="card">
<span class="card-num">課題感 ①</span>
<span class="card-tag">PAIN POINT</span>
<p class="card-text">体験の価値が高い ──<br>少し触るだけで、社内の理解は一気に進む</p>
</div>

<div class="card">
<span class="card-num">課題感 ②</span>
<span class="card-tag">PAIN POINT</span>
<p class="card-text">ハンズオン準備が大変 ──<br>調査・資料・手順書・告知文…手が回らない</p>
</div>

</div>

---

# Handson Hub Agent — 2つのスキル

生成AIの最新機能を題材に、**社内ハンズオンをすぐ開催できるところまで一気通貫**で支援するエージェント。

<div class="skill-box">
<div class="skill-label">SKILL 1</div><br>
<strong>/handson-research</strong>　ネタスカウト<br>
Anthropic 公式から直近1ヶ月の新機能を自動調査。<br>
ハンズオン適性でスコアリングし、候補 TOP3 を PPTX で出力。
</div>

<div class="skill-box">
<div class="skill-label">SKILL 2</div><br>
<strong>/handson-create {機能名}</strong>　一式生成<br>
スライド（7枚 PPTX）・参加者手順書・Teams 周知文を自動生成。<br>
コマンド1つで「今日の昼休みに開催できる状態」まで仕上げる。
</div>

---

# こだわったポイント

<div class="point-list">

<div class="point-item">
<div class="point-num">01</div>
<div class="point-body">
<p class="point-title">単なる資料作成ツールではなく、一気通貫で支援する</p>
<p class="point-desc">最新機能の発見 → スコアリング → スライド・手順書・告知文の生成まで、<br>エージェントがすべてつなぐ。「調べる・作る・展開する」が1コマンドで完結。</p>
</div>
</div>

<div class="point-item">
<div class="point-num">02</div>
<div class="point-body">
<p class="point-title">15分の昼休みでも開催できる「軽さ」を設計する</p>
<p class="point-desc">DX推進は本業の傍らで進めることが多い。重たい勉強会ではなく、<br>すぐ開けて、すぐ体験してもらえる小さな一歩を積み重ねる。</p>
</div>
</div>

</div>

---

<!-- _class: message -->

# おわりに

<div class="msg-quote">"</div>

<p class="msg-body">
情報そのものよりも、<strong style="color:#1a1a2e">人を巻き込んで、行動につなげられること</strong>の方が価値が高い時代。
</p>

<div class="msg-highlight">
「この人に聞けばAIのことがわかる」<br>
と思ってもらえる人を、社内に増やしたい。
</div>

<p class="msg-body" style="font-size:0.78rem;">
Handson Hub Agent は、エバンジェリストであり AI 活用の Hub になる人を支援するためのツールです。
</p>

<div class="msg-footer">AGI-Lab × AIエージェントハッカソン ／ 伊藤 カイ</div>

---
title: "タイピング速度テスト — 無料CPM測定ツール"
description: "タイピング速度と正確さをオンラインで測定。登録不要・ダウンロード不要。リアルタイムフィードバックで1分間の文字数（CPM）を即座に計測。"
date: 2025-05-16
categories: ["無料ツール"]
slug: "typing-speed-test"
ShowToc: false
aliases: ["/ja/tools/typing-test/", "/ja/tools/wpm-test/"]
cover:
  image: "/images/covers/typing-speed-test-ja.png"
  alt: "タイピング速度テスト"
---

<div id="type-app">

<style>
  #type-app {
    font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Hiragino Kaku Gothic ProN", "Noto Sans JP", sans-serif;
    max-width: 800px;
    margin: 0 auto;
    color: #e2e8f0;
  }
  #type-app * { box-sizing: border-box; }

  #type-app .ta-card {
    background: #1e293b;
    border: 1px solid #334155;
    border-radius: 12px;
    padding: 24px;
    margin-bottom: 20px;
  }

  #type-app .ta-controls {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    align-items: center;
    margin-bottom: 0;
  }

  #type-app .ta-control-group {
    display: flex;
    align-items: center;
    gap: 8px;
  }

  #type-app .ta-label {
    font-size: 13px;
    color: #94a3b8;
    font-weight: 500;
    white-space: nowrap;
  }

  #type-app .ta-btn-group {
    display: flex;
    gap: 4px;
  }

  #type-app .ta-btn {
    background: #0f172a;
    border: 1px solid #334155;
    color: #94a3b8;
    padding: 6px 14px;
    border-radius: 6px;
    cursor: pointer;
    font-size: 13px;
    font-weight: 500;
    transition: all 0.15s;
  }
  #type-app .ta-btn:hover {
    border-color: #2563eb;
    color: #60a5fa;
  }
  #type-app .ta-btn.active {
    background: #2563eb;
    border-color: #2563eb;
    color: #fff;
  }

  #type-app .ta-start-btn {
    background: #2563eb;
    border: none;
    color: #fff;
    padding: 8px 22px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 14px;
    font-weight: 600;
    transition: background 0.15s;
    margin-left: auto;
  }
  #type-app .ta-start-btn:hover { background: #1d4ed8; }
  #type-app .ta-start-btn:disabled { background: #475569; cursor: not-allowed; }

  #type-app .ta-progress-bar {
    height: 6px;
    background: #0f172a;
    border-radius: 3px;
    overflow: hidden;
    margin-bottom: 20px;
  }
  #type-app .ta-progress-fill {
    height: 100%;
    background: linear-gradient(90deg, #2563eb, #60a5fa);
    border-radius: 3px;
    transition: width 0.25s linear;
    width: 0%;
  }

  #type-app .ta-passage {
    font-size: 20px;
    line-height: 2.0;
    letter-spacing: 0.05em;
    background: #0f172a;
    border-radius: 10px;
    padding: 20px;
    margin-bottom: 16px;
    min-height: 110px;
    user-select: none;
    word-break: break-all;
  }

  #type-app .ta-char { color: #475569; }
  #type-app .ta-char.correct { color: #4ade80; }
  #type-app .ta-char.incorrect { color: #f87171; background: rgba(248,113,113,0.12); border-radius: 2px; }
  #type-app .ta-char.cursor {
    border-left: 2px solid #60a5fa;
    margin-left: -1px;
    padding-left: 1px;
    animation: ta-blink 1s step-end infinite;
  }
  @keyframes ta-blink { 0%,100%{opacity:1} 50%{opacity:0} }

  #type-app .ta-input {
    width: 100%;
    background: #0f172a;
    border: 2px solid #334155;
    border-radius: 8px;
    color: #e2e8f0;
    font-size: 16px;
    padding: 12px 16px;
    outline: none;
    transition: border-color 0.15s;
    resize: none;
    font-family: inherit;
    caret-color: #60a5fa;
  }
  #type-app .ta-input:focus { border-color: #2563eb; }
  #type-app .ta-input:disabled { opacity: 0.5; cursor: not-allowed; }

  #type-app .ta-timer-display {
    text-align: center;
    font-size: 48px;
    font-weight: 700;
    color: #60a5fa;
    font-variant-numeric: tabular-nums;
    margin: 4px 0;
  }
  #type-app .ta-timer-label {
    text-align: center;
    font-size: 12px;
    color: #64748b;
    text-transform: uppercase;
    letter-spacing: 0.1em;
  }

  #type-app .ta-stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 12px;
    margin-top: 4px;
  }
  @media (max-width: 600px) {
    #type-app .ta-stats-grid { grid-template-columns: repeat(2, 1fr); }
  }

  #type-app .ta-stat {
    background: #0f172a;
    border-radius: 10px;
    padding: 14px;
    text-align: center;
  }
  #type-app .ta-stat-val {
    font-size: 28px;
    font-weight: 700;
    color: #60a5fa;
    font-variant-numeric: tabular-nums;
  }
  #type-app .ta-stat-lbl {
    font-size: 11px;
    color: #64748b;
    letter-spacing: 0.04em;
    margin-top: 2px;
  }

  #type-app .ta-result-card {
    background: #1e293b;
    border: 1px solid #2563eb44;
    border-radius: 12px;
    padding: 28px;
    text-align: center;
    display: none;
  }
  #type-app .ta-result-card.visible { display: block; }
  #type-app .ta-result-title {
    font-size: 22px;
    font-weight: 700;
    color: #e2e8f0;
    margin-bottom: 20px;
  }
  #type-app .ta-result-cpm {
    font-size: 64px;
    font-weight: 800;
    color: #60a5fa;
    line-height: 1;
  }
  #type-app .ta-result-cpm-lbl {
    font-size: 14px;
    color: #94a3b8;
    margin-bottom: 20px;
    margin-top: 4px;
  }
  #type-app .ta-result-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
    margin-bottom: 24px;
  }
  @media (max-width: 500px) {
    #type-app .ta-result-grid { grid-template-columns: repeat(1, 1fr); }
  }

  #type-app .ta-retry-btn {
    background: #2563eb;
    border: none;
    color: #fff;
    padding: 10px 32px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 15px;
    font-weight: 600;
    transition: background 0.15s;
  }
  #type-app .ta-retry-btn:hover { background: #1d4ed8; }

  #type-app .ta-history {
    margin-top: 4px;
  }
  #type-app .ta-history-title {
    font-size: 14px;
    font-weight: 600;
    color: #94a3b8;
    margin-bottom: 10px;
    letter-spacing: 0.04em;
  }
  #type-app .ta-history-empty {
    color: #475569;
    font-size: 13px;
    text-align: center;
    padding: 16px;
  }
  #type-app .ta-history-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
  }
  #type-app .ta-history-table th {
    color: #64748b;
    font-weight: 500;
    text-align: left;
    padding: 6px 10px;
    border-bottom: 1px solid #1e293b;
  }
  #type-app .ta-history-table td {
    padding: 8px 10px;
    color: #cbd5e1;
    border-bottom: 1px solid #1e293b22;
  }
  #type-app .ta-history-table tr:last-child td { border-bottom: none; }
  #type-app .ta-history-clear {
    background: none;
    border: 1px solid #334155;
    color: #64748b;
    padding: 4px 10px;
    border-radius: 5px;
    cursor: pointer;
    font-size: 12px;
    float: right;
    transition: all 0.15s;
  }
  #type-app .ta-history-clear:hover { border-color: #f87171; color: #f87171; }

  #type-app .ta-msg {
    font-size: 13px;
    color: #64748b;
    text-align: center;
    padding: 8px 0 0;
  }

  /* freee CTA */
  #type-app .ta-cta {
    background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
    border: 1px solid #2563eb55;
    border-radius: 12px;
    padding: 24px 28px;
    margin-top: 8px;
    display: flex;
    align-items: center;
    gap: 20px;
    flex-wrap: wrap;
  }
  #type-app .ta-cta-text { flex: 1; min-width: 200px; }
  #type-app .ta-cta-title {
    font-size: 16px;
    font-weight: 700;
    color: #e2e8f0;
    margin-bottom: 6px;
  }
  #type-app .ta-cta-desc {
    font-size: 13px;
    color: #94a3b8;
    line-height: 1.6;
  }
  #type-app .ta-cta-btn {
    background: #2563eb;
    color: #fff;
    border: none;
    border-radius: 8px;
    padding: 10px 24px;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    text-decoration: none;
    display: inline-block;
    white-space: nowrap;
    transition: background 0.15s;
  }
  #type-app .ta-cta-btn:hover { background: #1d4ed8; }
</style>

<!-- Controls -->
<div class="ta-card">
  <div class="ta-controls">
    <div class="ta-control-group">
      <span class="ta-label">制限時間</span>
      <div class="ta-btn-group" id="ta-dur-group">
        <button class="ta-btn" data-dur="30">30秒</button>
        <button class="ta-btn active" data-dur="60">60秒</button>
        <button class="ta-btn" data-dur="120">120秒</button>
      </div>
    </div>
    <div class="ta-control-group">
      <span class="ta-label">難易度</span>
      <div class="ta-btn-group" id="ta-diff-group">
        <button class="ta-btn active" data-diff="easy">かんたん</button>
        <button class="ta-btn" data-diff="medium">ふつう</button>
        <button class="ta-btn" data-diff="hard">むずかしい</button>
      </div>
    </div>
    <button class="ta-start-btn" id="ta-reset-btn">リセット</button>
  </div>
</div>

<!-- Timer + Progress -->
<div class="ta-card" style="padding:16px 24px;">
  <div class="ta-timer-label">残り時間</div>
  <div class="ta-timer-display" id="ta-timer">60</div>
  <div class="ta-progress-bar">
    <div class="ta-progress-fill" id="ta-progress"></div>
  </div>
  <div class="ta-stats-grid">
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-cpm-live">0</div>
      <div class="ta-stat-lbl">CPM（文字/分）</div>
    </div>
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-acc-live">—</div>
      <div class="ta-stat-lbl">正確率</div>
    </div>
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-chars-live">0</div>
      <div class="ta-stat-lbl">打鍵数</div>
    </div>
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-errors-live">0</div>
      <div class="ta-stat-lbl">ミス数</div>
    </div>
  </div>
</div>

<!-- Passage + Input -->
<div class="ta-card">
  <div class="ta-passage" id="ta-passage" aria-label="入力するテキスト"></div>
  <textarea
    class="ta-input"
    id="ta-input"
    rows="3"
    placeholder="ここをクリックして入力を開始するとタイマーが始まります…"
    autocomplete="off"
    autocorrect="off"
    autocapitalize="off"
    spellcheck="false"
  ></textarea>
  <p class="ta-msg" id="ta-msg">最初のキー入力でタイマーがスタートします。</p>
</div>

<!-- Result -->
<div class="ta-result-card" id="ta-result">
  <div class="ta-result-title">テスト完了！</div>
  <div class="ta-result-cpm" id="ta-res-cpm">0</div>
  <div class="ta-result-cpm-lbl">1分あたりの文字数（CPM）</div>
  <div class="ta-result-grid">
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-res-acc">0%</div>
      <div class="ta-stat-lbl">正確率</div>
    </div>
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-res-time">0秒</div>
      <div class="ta-stat-lbl">経過時間</div>
    </div>
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-res-chars">0</div>
      <div class="ta-stat-lbl">打鍵数</div>
    </div>
  </div>
  <button class="ta-retry-btn" id="ta-retry-btn">もう一度挑戦</button>
</div>

<!-- History -->
<div class="ta-card ta-history" id="ta-history-card">
  <div class="ta-history-title">
    過去の結果
    <button class="ta-history-clear" id="ta-clear-hist">クリア</button>
  </div>
  <div id="ta-history-body"></div>
</div>

<!-- freee CTA -->
<div class="ta-cta">
  <div class="ta-cta-text">
    <div class="ta-cta-title">freee で経理・給与計算を自動化しませんか？</div>
    <div class="ta-cta-desc">タイピングスピードが上がっても、入力業務そのものをなくす方が効果的。freeeなら請求書・経費・給与を自動処理。バックオフィスの時間を本来の仕事に。</div>
  </div>
  <a class="ta-cta-btn" href="https://www.freee.co.jp/" target="_blank" rel="noopener">freeeを無料で試す</a>
</div>

<script>
(function(){
  // ─── 文章データ ───────────────────────────────────────────────────────────────
  const PASSAGES = {
    easy: [
      "あいうえお かきくけこ さしすせそ たちつてと なにぬねの はひふへほ まみむめも やゆよ らりるれろ わをん",
      "はるはあけぼの やうやうしろくなりゆくやまぎわ すこしあかりて むらさきだちたるくもの ほそくたなびきたる",
      "ふるいけや かわずとびこむ みずのおと まつおばしょうのはいく せかいにしられた にほんのしぜんびがあふれる",
      "きょうはいいてんきです あおいそらに しろいくもが うかんでいます こどもたちが こうえんであそんでいます",
      "むかしむかし あるところに おじいさんと おばあさんが いました ふたりはなかよく くらしていました",
      "さくらのはなが さいています はるのかぜが やさしくふいて はなびらが まいあがっています",
      "やまのむこうに おひさまが しずんでいきます そらがあかくそまり うつくしいゆうやけです",
      "かわのながれは とまることなく つづいていきます いのちのながれも おなじようなものです",
      "たなかさんは まいあさ ろくじにおきます そして ジョギングをしてから しごとにいきます",
      "でんしゃにのって しごとにいく とちゅうで ほんをよむ それがわたしの まいにちのたのしみです",
    ],
    medium: [
      "生産性を高めるには、正しいことに集中し、不要な作業を排除し、質の高い休息をとることが重要です。速さだけを追い求めても、方向性が間違っていては意味がありません。",
      "タイピングの速度は、繰り返しの練習だけでは伸びません。正確さを意識しながら練習することで、筋肉の記憶が定着し、自然と速度が上がっていきます。",
      "朝のルーティンを確立することで、一日の生産性が大きく変わります。起床時刻を一定にし、最初の30分はスマートフォンを見ずに過ごすことをお勧めします。",
      "集中力を維持するには、作業と休憩のバランスが大切です。25分作業して5分休む「ポモドーロ・テクニック」は多くの人に効果的とされています。",
      "読書は思考を広げ、異なる分野のアイデアをつなげる力を養います。週に一冊の本を読む習慣は、長期的な知識の蓄積につながります。",
      "デジタルツールは使い方次第で生産性を上げも下げもします。通知をオフにし、必要なときだけメールを確認するだけで、集中力は大幅に向上します。",
      "目標を紙に書き出すことで、達成率が高まるという研究があります。具体的で測定可能な目標を設定し、進捗を定期的に振り返る習慣をつけましょう。",
      "チームの生産性を高めるためには、明確なコミュニケーションと役割分担が欠かせません。会議の目的を明確にし、必要な人だけが参加する仕組みを作りましょう。",
      "仕事の優先順位をつけるとき、緊急度と重要度のマトリックスが役立ちます。重要だが緊急ではないことに時間を使うことが、長期的な成功につながります。",
      "睡眠は生産性の基盤です。7〜8時間の質の高い睡眠は、集中力、記憶力、判断力を大幅に向上させます。徹夜は短期的な成果よりも長期的な損失が大きいです。",
    ],
    hard: [
      "機械学習モデルの訓練においては、損失関数の勾配を各パラメータに関して偏微分し、その勾配の反対方向にパラメータを更新する確率的勾配降下法が広く用いられています。",
      "量子コンピュータは、重ね合わせと量子もつれを利用して、従来のビット演算では指数関数的な時間を要する問題を多項式時間で解ける可能性を持っています。",
      "ブロックチェーン技術は、分散型台帳にトランザクションを記録し、暗号学的ハッシュ関数によってデータの改ざんを防ぐ仕組みで、金融・物流・医療など幅広い分野での活用が進んでいます。",
      "Kubernetesは、コンテナ化されたアプリケーションのデプロイ・スケーリング・管理を自動化するオーケストレーションシステムで、宣言的な設定ファイルによってインフラを管理します。",
      "ゼロ知識証明は、ある命題が真であることを、命題の内容に関する情報を一切開示せずに証明できる暗号プロトコルであり、プライバシー保護型認証システムの基盤となっています。",
      "マイクロサービスアーキテクチャでは、アプリケーションを独立してデプロイ可能な小さなサービスに分割し、APIを通じて通信させることで、スケーラビリティと保守性を高めます。",
      "トランスフォーマーアーキテクチャは、自己注意機構を用いてトークン間の依存関係を並列に計算することで、自然言語処理における革命的な性能向上をもたらしました。",
      "差分プライバシーは、統計的なクエリ結果にキャリブレーションされたノイズを加えることで、個々のレコードが推定されないことを数学的に保証するプライバシー保護手法です。",
      "コンパイラは、字句解析・構文解析・意味解析・中間表現生成・最適化・コード生成という各フェーズを経て、高水準言語のソースコードを機械語に変換するシステムソフトウェアです。",
      "分散合意プロトコルであるRaftは、リーダー選出とログ複製によってフォールトトレランスを実現し、少数のノード障害が発生してもシステム全体の一貫性を維持します。",
    ],
  };

  // ─── 状態 ────────────────────────────────────────────────────────────────────
  let duration = 60;
  let difficulty = "easy";
  let passage = "";
  let totalTyped = 0;
  let totalErrors = 0;
  let startTime = null;
  let timerInterval = null;
  let running = false;
  let finished = false;

  // ─── 要素 ────────────────────────────────────────────────────────────────────
  const elPassage    = document.getElementById("ta-passage");
  const elInput      = document.getElementById("ta-input");
  const elTimer      = document.getElementById("ta-timer");
  const elProgress   = document.getElementById("ta-progress");
  const elCpmLive    = document.getElementById("ta-cpm-live");
  const elAccLive    = document.getElementById("ta-acc-live");
  const elCharsLive  = document.getElementById("ta-chars-live");
  const elErrorsLive = document.getElementById("ta-errors-live");
  const elResult     = document.getElementById("ta-result");
  const elResCpm     = document.getElementById("ta-res-cpm");
  const elResAcc     = document.getElementById("ta-res-acc");
  const elResTime    = document.getElementById("ta-res-time");
  const elResChars   = document.getElementById("ta-res-chars");
  const elMsg        = document.getElementById("ta-msg");
  const elRetryBtn   = document.getElementById("ta-retry-btn");
  const elResetBtn   = document.getElementById("ta-reset-btn");
  const elHistBody   = document.getElementById("ta-history-body");
  const elClearHist  = document.getElementById("ta-clear-hist");

  // ─── ヘルパー ─────────────────────────────────────────────────────────────────
  function pickPassage() {
    const pool = PASSAGES[difficulty];
    return pool[Math.floor(Math.random() * pool.length)];
  }

  function renderPassage() {
    elPassage.innerHTML = passage.split("").map((ch, i) => {
      let cls = "ta-char";
      if (i === 0) cls += " cursor";
      const display = ch === " " ? "&nbsp;" : ch;
      return `<span class="${cls}" data-i="${i}">${display}</span>`;
    }).join("");
  }

  function updatePassageDisplay(typed) {
    const spans = elPassage.querySelectorAll(".ta-char");
    spans.forEach((s, i) => {
      s.className = "ta-char";
      if (i < typed.length) {
        s.classList.add(typed[i] === passage[i] ? "correct" : "incorrect");
      }
      if (i === typed.length) s.classList.add("cursor");
    });
  }

  function calcCpm(elapsed) {
    // CPM: 打鍵数 / 分
    const minutes = elapsed / 60000;
    if (minutes === 0) return 0;
    return Math.round(totalTyped / minutes);
  }

  function calcAcc() {
    if (totalTyped === 0) return null;
    return Math.round(((totalTyped - totalErrors) / totalTyped) * 100);
  }

  function updateLiveStats() {
    const elapsed = Date.now() - startTime;
    elCpmLive.textContent = calcCpm(elapsed);
    const acc = calcAcc();
    elAccLive.textContent = acc !== null ? acc + "%" : "—";
    elCharsLive.textContent = totalTyped;
    elErrorsLive.textContent = totalErrors;
  }

  function startTimer() {
    startTime = Date.now();
    running = true;
    elMsg.textContent = "テスト中…";

    timerInterval = setInterval(() => {
      const elapsed = Date.now() - startTime;
      const remaining = Math.max(0, duration * 1000 - elapsed);
      const secs = Math.ceil(remaining / 1000);
      elTimer.textContent = secs;
      elProgress.style.width = ((1 - remaining / (duration * 1000)) * 100) + "%";
      updateLiveStats();

      if (remaining <= 0) {
        clearInterval(timerInterval);
        finishTest();
      }
    }, 100);
  }

  function finishTest() {
    running = false;
    finished = true;
    elInput.disabled = true;
    const elapsed = startTime ? Date.now() - startTime : duration * 1000;
    const actualSecs = Math.min(Math.round(elapsed / 1000), duration);
    const cpm = calcCpm(Math.min(elapsed, duration * 1000));
    const acc = calcAcc();

    elResCpm.textContent = cpm;
    elResAcc.textContent = (acc !== null ? acc : 0) + "%";
    elResTime.textContent = actualSecs + "秒";
    elResChars.textContent = totalTyped;
    elResult.classList.add("visible");
    elMsg.textContent = "テスト完了！";

    saveHistory({ cpm, acc: acc ?? 0, time: actualSecs, chars: totalTyped, diff: difficulty, dur: duration });
    renderHistory();
  }

  function reset() {
    clearInterval(timerInterval);
    running = false;
    finished = false;
    totalTyped = 0;
    totalErrors = 0;
    startTime = null;
    passage = pickPassage();
    elInput.value = "";
    elInput.disabled = false;
    elInput.focus();
    elTimer.textContent = duration;
    elProgress.style.width = "0%";
    elCpmLive.textContent = "0";
    elAccLive.textContent = "—";
    elCharsLive.textContent = "0";
    elErrorsLive.textContent = "0";
    elResult.classList.remove("visible");
    elMsg.textContent = "最初のキー入力でタイマーがスタートします。";
    renderPassage();
  }

  // ─── 入力処理 ──────────────────────────────────────────────────────────────
  elInput.addEventListener("input", function() {
    if (finished) return;
    const typed = this.value;

    if (!running && typed.length > 0) startTimer();
    if (!running && typed.length === 0) return;

    const clamped = typed.slice(0, passage.length);

    totalTyped = clamped.length;
    totalErrors = 0;
    for (let i = 0; i < clamped.length; i++) {
      if (clamped[i] !== passage[i]) totalErrors++;
    }

    updatePassageDisplay(clamped);
    updateLiveStats();

    // パッセージ完了時に次のパッセージへ
    if (clamped.length === passage.length && running) {
      passage = pickPassage();
      this.value = "";
      renderPassage();
    }
  });

  // ペースト禁止
  elInput.addEventListener("paste", e => e.preventDefault());

  // ─── コントロール ─────────────────────────────────────────────────────────────
  document.getElementById("ta-dur-group").addEventListener("click", e => {
    const btn = e.target.closest("[data-dur]");
    if (!btn) return;
    document.querySelectorAll("#ta-dur-group .ta-btn").forEach(b => b.classList.remove("active"));
    btn.classList.add("active");
    duration = parseInt(btn.dataset.dur);
    reset();
  });

  document.getElementById("ta-diff-group").addEventListener("click", e => {
    const btn = e.target.closest("[data-diff]");
    if (!btn) return;
    document.querySelectorAll("#ta-diff-group .ta-btn").forEach(b => b.classList.remove("active"));
    btn.classList.add("active");
    difficulty = btn.dataset.diff;
    reset();
  });

  elResetBtn.addEventListener("click", reset);
  elRetryBtn.addEventListener("click", reset);

  // ─── 履歴 ────────────────────────────────────────────────────────────────────
  const HIST_KEY = "ta_history_ja";

  function saveHistory(entry) {
    const hist = getHistory();
    hist.unshift({ ...entry, date: new Date().toLocaleDateString("ja-JP") });
    if (hist.length > 15) hist.length = 15;
    localStorage.setItem(HIST_KEY, JSON.stringify(hist));
  }

  function getHistory() {
    try { return JSON.parse(localStorage.getItem(HIST_KEY)) || []; }
    catch { return []; }
  }

  const DIFF_LABEL = { easy: "かんたん", medium: "ふつう", hard: "むずかしい" };

  function renderHistory() {
    const hist = getHistory();
    if (hist.length === 0) {
      elHistBody.innerHTML = '<div class="ta-history-empty">まだ記録がありません。テストを完了すると履歴が表示されます。</div>';
      return;
    }
    elHistBody.innerHTML = `<table class="ta-history-table">
      <thead><tr>
        <th>#</th><th>CPM</th><th>正確率</th><th>時間</th><th>打鍵数</th><th>難易度</th><th>日付</th>
      </tr></thead>
      <tbody>${hist.map((r, i) => `<tr>
        <td>${i + 1}</td>
        <td><strong style="color:#60a5fa">${r.cpm}</strong></td>
        <td>${r.acc}%</td>
        <td>${r.time}秒 / ${r.dur}秒</td>
        <td>${r.chars}</td>
        <td>${DIFF_LABEL[r.diff] || r.diff}</td>
        <td>${r.date}</td>
      </tr>`).join("")}</tbody>
    </table>`;
  }

  elClearHist.addEventListener("click", () => {
    localStorage.removeItem(HIST_KEY);
    renderHistory();
  });

  // ─── 初期化 ──────────────────────────────────────────────────────────────────
  reset();
  renderHistory();
})();
</script>

</div>

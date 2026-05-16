---
title: "メール署名ジェネレーター — 無料プロフェッショナルツール"
date: 2025-05-16
description: "ライブプレビュー付きでプロフェッショナルなメール署名を作成。ビジネス・クリエイティブ・ミニマルのテンプレート。Gmail・Outlook・Apple Mail用HTMLをコピー。"
categories: ["無料ツール"]
slug: "email-signature-generator"
ShowToc: false
cover:
  image: "/images/covers/email-signature-generator-ja.png"
  alt: "メール署名ジェネレーター"
---

アカウント登録不要・データ送信なし。情報を入力してテンプレートを選ぶだけで、プロフェッショナルなメール署名をすぐに作成できます。生成されたHTMLをGmail・Outlook・Apple Mailにそのまま貼り付けて使用してください。

<div id="sig-app">
<style>
/* ── スコープ済みスタイル: すべてのセレクターに #sig-app プレフィックス ── */
#sig-app *,
#sig-app *::before,
#sig-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#sig-app {
  font-family: "Hiragino Sans", "Hiragino Kaku Gothic ProN", "Noto Sans JP", "Yu Gothic", Meiryo, -apple-system, sans-serif;
  font-size: 15px;
  color: #1a1a1a;
  line-height: 1.6;
  max-width: 960px;
  margin: 0 auto;
  padding: 0 16px 48px;
}

/* ── レイアウトグリッド ── */
#sig-app .sa-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 32px;
  margin-top: 32px;
}
@media (max-width: 680px) {
  #sig-app .sa-grid { grid-template-columns: 1fr; }
}

/* ── パネルカード ── */
#sig-app .sa-panel {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 24px;
}
#sig-app .sa-panel h2 {
  font-size: .9rem;
  font-weight: 700;
  letter-spacing: .04em;
  margin-bottom: 18px;
  color: #0f172a;
  text-transform: uppercase;
}

/* ── フォームコントロール ── */
#sig-app .sa-field { margin-bottom: 14px; }
#sig-app .sa-field label {
  display: block;
  font-size: .75rem;
  font-weight: 600;
  color: #475569;
  margin-bottom: 4px;
}
#sig-app .sa-field input,
#sig-app .sa-field select {
  width: 100%;
  padding: 8px 11px;
  border: 1px solid #cbd5e1;
  border-radius: 7px;
  font-size: .92rem;
  color: #1e293b;
  background: #f8fafc;
  outline: none;
  transition: border-color .15s;
  font-family: inherit;
}
#sig-app .sa-field input:focus,
#sig-app .sa-field select:focus {
  border-color: #6366f1;
  background: #fff;
}

/* ── テンプレートボタン ── */
#sig-app .sa-templates {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
  margin-bottom: 18px;
}
#sig-app .sa-tpl-btn {
  padding: 6px 14px;
  border: 2px solid #e2e8f0;
  border-radius: 20px;
  background: #f8fafc;
  font-size: .82rem;
  font-weight: 600;
  cursor: pointer;
  transition: all .15s;
  color: #475569;
  font-family: inherit;
}
#sig-app .sa-tpl-btn:hover { border-color: #6366f1; color: #6366f1; }
#sig-app .sa-tpl-btn.active {
  border-color: #6366f1;
  background: #6366f1;
  color: #fff;
}

/* ── プレビューエリア ── */
#sig-app .sa-preview-wrap {
  background: #f1f5f9;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 24px;
  min-height: 160px;
}
#sig-app .sa-preview-label {
  font-size: .72rem;
  font-weight: 700;
  color: #94a3b8;
  letter-spacing: .06em;
  margin-bottom: 12px;
  text-transform: uppercase;
}

/* ── アクションボタン ── */
#sig-app .sa-actions { display: flex; gap: 10px; margin-top: 16px; flex-wrap: wrap; }
#sig-app .sa-btn {
  padding: 9px 20px;
  border-radius: 8px;
  font-size: .88rem;
  font-weight: 700;
  cursor: pointer;
  border: none;
  transition: opacity .15s;
  font-family: inherit;
}
#sig-app .sa-btn:hover { opacity: .85; }
#sig-app .sa-btn-primary { background: #6366f1; color: #fff; }
#sig-app .sa-btn-secondary { background: #e2e8f0; color: #1e293b; }
#sig-app .sa-btn-success { background: #22c55e; color: #fff; }

/* ── トースト通知 ── */
#sig-app .sa-toast {
  display: none;
  background: #22c55e;
  color: #fff;
  padding: 8px 16px;
  border-radius: 6px;
  font-size: .85rem;
  font-weight: 600;
  margin-top: 10px;
}
#sig-app .sa-toast.show { display: inline-block; }

/* ── HTML出力 ── */
#sig-app .sa-html-out {
  width: 100%;
  margin-top: 12px;
  font-family: "Courier New", monospace;
  font-size: .78rem;
  padding: 12px;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  background: #0f172a;
  color: #a5f3fc;
  resize: vertical;
  min-height: 120px;
  display: none;
}

/* ── 手順アコーディオン ── */
#sig-app .sa-instr { margin-top: 32px; }
#sig-app .sa-instr-title {
  font-size: 1.05rem;
  font-weight: 700;
  margin-bottom: 16px;
  color: #0f172a;
}
#sig-app .sa-accordion summary {
  cursor: pointer;
  padding: 12px 16px;
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  font-weight: 600;
  font-size: .92rem;
  list-style: none;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 4px;
  transition: background .15s;
  font-family: inherit;
}
#sig-app .sa-accordion summary:hover { background: #ede9fe; }
#sig-app .sa-accordion summary::after { content: "▸"; font-size: .8rem; }
#sig-app .sa-accordion[open] summary::after { content: "▾"; }
#sig-app .sa-accordion .sa-acc-body {
  padding: 14px 16px;
  border: 1px solid #e2e8f0;
  border-top: none;
  border-radius: 0 0 8px 8px;
  margin-bottom: 8px;
  font-size: .88rem;
  line-height: 1.8;
  color: #334155;
}
#sig-app .sa-acc-body ol { padding-left: 20px; }
#sig-app .sa-acc-body li { margin-bottom: 6px; }

/* ── 関連ツール ── */
#sig-app .sa-related {
  margin-top: 40px;
  padding-top: 24px;
  border-top: 1px solid #e2e8f0;
}
#sig-app .sa-related h3 { font-size: .95rem; font-weight: 700; margin-bottom: 12px; color: #0f172a; }
#sig-app .sa-related ul { list-style: none; display: flex; gap: 12px; flex-wrap: wrap; }
#sig-app .sa-related a {
  color: #6366f1;
  font-weight: 600;
  font-size: .88rem;
  text-decoration: none;
  border: 1px solid #c7d2fe;
  padding: 5px 12px;
  border-radius: 20px;
  transition: all .15s;
}
#sig-app .sa-related a:hover { background: #6366f1; color: #fff; }

/* ── カラースウォッチ ── */
#sig-app .sa-swatches { display: flex; gap: 8px; flex-wrap: wrap; }
#sig-app .sa-swatch {
  width: 28px; height: 28px;
  border-radius: 50%;
  border: 3px solid transparent;
  cursor: pointer;
  transition: border-color .15s;
}
#sig-app .sa-swatch.active { border-color: #0f172a; }

/* ── freee CTA ── */
#sig-app .sa-freee-cta {
  margin-top: 40px;
  padding: 24px 28px;
  background: linear-gradient(135deg, #ede9fe 0%, #dbeafe 100%);
  border: 1px solid #c7d2fe;
  border-radius: 12px;
  display: flex;
  align-items: center;
  gap: 20px;
  flex-wrap: wrap;
}
#sig-app .sa-freee-cta-text { flex: 1; min-width: 200px; }
#sig-app .sa-freee-cta-text strong {
  display: block;
  font-size: 1rem;
  font-weight: 700;
  color: #1e293b;
  margin-bottom: 4px;
}
#sig-app .sa-freee-cta-text p {
  font-size: .88rem;
  color: #475569;
  line-height: 1.6;
}
#sig-app .sa-freee-cta-btn {
  display: inline-block;
  padding: 10px 22px;
  background: #6366f1;
  color: #fff;
  font-weight: 700;
  font-size: .92rem;
  border-radius: 8px;
  text-decoration: none;
  white-space: nowrap;
  transition: opacity .15s;
}
#sig-app .sa-freee-cta-btn:hover { opacity: .85; }
</style>

<div class="sa-grid">
  <!-- ── 左: 入力フォーム ── -->
  <div>
    <div class="sa-panel">
      <h2>署名情報を入力</h2>

      <div class="sa-field">
        <label>氏名</label>
        <input type="text" id="sa-name" placeholder="山田 太郎" oninput="saRender()">
      </div>
      <div class="sa-field">
        <label>役職</label>
        <input type="text" id="sa-title" placeholder="シニアプロダクトデザイナー" oninput="saRender()">
      </div>
      <div class="sa-field">
        <label>会社名</label>
        <input type="text" id="sa-company" placeholder="株式会社〇〇" oninput="saRender()">
      </div>
      <div class="sa-field">
        <label>電話番号</label>
        <input type="text" id="sa-phone" placeholder="03-0000-0000" oninput="saRender()">
      </div>
      <div class="sa-field">
        <label>メールアドレス</label>
        <input type="email" id="sa-email" placeholder="taro@example.co.jp" oninput="saRender()">
      </div>
      <div class="sa-field">
        <label>ウェブサイト</label>
        <input type="text" id="sa-website" placeholder="https://example.co.jp" oninput="saRender()">
      </div>
      <div class="sa-field">
        <label>LinkedIn URL</label>
        <input type="text" id="sa-linkedin" placeholder="https://linkedin.com/in/taro-yamada" oninput="saRender()">
      </div>
      <div class="sa-field">
        <label>Twitter / X アカウント</label>
        <input type="text" id="sa-twitter" placeholder="@taro_yamada" oninput="saRender()">
      </div>
      <div class="sa-field">
        <label>GitHub ユーザー名</label>
        <input type="text" id="sa-github" placeholder="taro-yamada" oninput="saRender()">
      </div>
    </div>

    <div class="sa-panel" style="margin-top:20px;">
      <h2>スタイル設定</h2>

      <div class="sa-field">
        <label>レイアウト</label>
        <select id="sa-layout" onchange="saRender()">
          <option value="horizontal">横並び（写真左・テキスト右）</option>
          <option value="vertical">縦並び（積み重ね）</option>
        </select>
      </div>

      <div class="sa-field">
        <label>カラーテーマ</label>
        <div class="sa-swatches" id="sa-swatches">
          <span class="sa-swatch active" data-color="#6366f1" style="background:#6366f1" onclick="saPick(this)"></span>
          <span class="sa-swatch" data-color="#0ea5e9" style="background:#0ea5e9" onclick="saPick(this)"></span>
          <span class="sa-swatch" data-color="#10b981" style="background:#10b981" onclick="saPick(this)"></span>
          <span class="sa-swatch" data-color="#f59e0b" style="background:#f59e0b" onclick="saPick(this)"></span>
          <span class="sa-swatch" data-color="#ef4444" style="background:#ef4444" onclick="saPick(this)"></span>
          <span class="sa-swatch" data-color="#8b5cf6" style="background:#8b5cf6" onclick="saPick(this)"></span>
          <span class="sa-swatch" data-color="#1e293b" style="background:#1e293b" onclick="saPick(this)"></span>
          <span class="sa-swatch" data-color="#64748b" style="background:#64748b" onclick="saPick(this)"></span>
        </div>
      </div>

      <div class="sa-field">
        <label>フォント</label>
        <select id="sa-font" onchange="saRender()">
          <option value="Arial, Helvetica, sans-serif">Arial（標準・安全）</option>
          <option value="Georgia, serif">Georgia（クラシック）</option>
          <option value="'Courier New', monospace">Courier New（開発者向け）</option>
          <option value="Verdana, Geneva, sans-serif">Verdana</option>
          <option value="Trebuchet MS, sans-serif">Trebuchet MS</option>
        </select>
      </div>

      <div class="sa-field">
        <label>区切り線のスタイル</label>
        <select id="sa-sep" onchange="saRender()">
          <option value="solid">実線</option>
          <option value="dashed">破線</option>
          <option value="dotted">点線</option>
          <option value="none">なし</option>
        </select>
      </div>

      <div class="sa-field">
        <label>写真プレースホルダー</label>
        <select id="sa-photo" onchange="saRender()">
          <option value="circle">円形アバター</option>
          <option value="square">正方形アバター</option>
          <option value="none">なし</option>
        </select>
      </div>
    </div>
  </div>

  <!-- ── 右: テンプレート選択・プレビュー ── -->
  <div>
    <div class="sa-panel">
      <h2>テンプレート</h2>
      <div class="sa-templates">
        <button class="sa-tpl-btn active" onclick="saSetTpl('corporate',this)">ビジネス</button>
        <button class="sa-tpl-btn" onclick="saSetTpl('creative',this)">クリエイティブ</button>
        <button class="sa-tpl-btn" onclick="saSetTpl('minimal',this)">ミニマル</button>
        <button class="sa-tpl-btn" onclick="saSetTpl('developer',this)">開発者</button>
      </div>

      <div class="sa-preview-label">ライブプレビュー</div>
      <div class="sa-preview-wrap">
        <div id="sa-preview"></div>
      </div>

      <div class="sa-actions">
        <button class="sa-btn sa-btn-primary" onclick="saCopyHTML()">HTMLをコピー</button>
        <button class="sa-btn sa-btn-secondary" onclick="saToggleCode()">HTMLを表示</button>
        <button class="sa-btn sa-btn-secondary" onclick="saReset()">リセット</button>
      </div>
      <span class="sa-toast" id="sa-toast">クリップボードにコピーしました！</span>
      <textarea class="sa-html-out" id="sa-html-out" readonly></textarea>
    </div>
  </div>
</div>

<!-- ── 設置手順 ── -->
<div class="sa-instr">
  <div class="sa-instr-title">メールクライアントへの設置方法</div>

  <details class="sa-accordion">
    <summary>Gmail への設置手順</summary>
    <div class="sa-acc-body">
      <ol>
        <li>上の「<strong>HTMLをコピー</strong>」ボタンをクリックします。</li>
        <li>Gmailを開き、右上の歯車アイコン → 「<strong>すべての設定を表示</strong>」をクリック。</li>
        <li>「<strong>全般</strong>」タブを開き、「<strong>署名</strong>」セクションまでスクロールして「<strong>新規作成</strong>」をクリック。</li>
        <li>署名名を入力（例：「ビジネス用」）し、署名入力欄の中をクリック。</li>
        <li>ツールバー内の「⋮ その他のオプション」→「<strong>HTMLとして編集</strong>」を選択。</li>
        <li>コピーしたHTMLを貼り付けて「<strong>OK</strong>」をクリック。</li>
        <li>ページ下部の「<strong>変更を保存</strong>」をクリックして完了。</li>
      </ol>
    </div>
  </details>

  <details class="sa-accordion">
    <summary>Outlook（Windows・Mac）への設置手順</summary>
    <div class="sa-acc-body">
      <ol>
        <li>上の「<strong>HTMLをコピー</strong>」ボタンをクリックします。</li>
        <li>Outlookで「<strong>新しいメール</strong>」を開く。</li>
        <li>「<strong>挿入</strong>」→「<strong>署名</strong>」→「<strong>署名…</strong>」を選択。</li>
        <li>「<strong>新規</strong>」をクリックして名前を付け、編集エリアをクリック。</li>
        <li>メモ帳にHTMLを貼り付けて <code>sig.htm</code> として保存。</li>
        <li>Outlook署名エディターの「ソース / HTML」ボタンからHTMLを貼り付けるか、保存した <code>.htm</code> ファイルをドラッグ。</li>
        <li>「<strong>OK</strong>」をクリックし、必要に応じてデフォルト署名として設定して完了。</li>
      </ol>
    </div>
  </details>

  <details class="sa-accordion">
    <summary>Apple Mail（macOS）への設置手順</summary>
    <div class="sa-acc-body">
      <ol>
        <li>上の「<strong>HTMLをコピー</strong>」ボタンをクリックします。</li>
        <li>「<strong>メール</strong>」→「<strong>設定</strong>」→「<strong>署名</strong>」を開く。</li>
        <li>アカウントを選択して「<strong>+</strong>」で新しい署名を追加。</li>
        <li>署名本文に仮のテキスト（例：「x」）を入力してメールを終了。</li>
        <li>ターミナルを開いて <code>open ~/Library/Mail</code> を実行。</li>
        <li>「V10（またはご使用のバージョン）→ アカウントフォルダ → Data → Signatures」に移動。</li>
        <li><code>.mailsignature</code> ファイルをテキストエディターで開き、仮テキスト部分をコピーしたHTMLに置き換えて保存。</li>
        <li>メールを再起動して完了。</li>
      </ol>
    </div>
  </details>
</div>

<!-- ── 関連ツール ── -->
<div class="sa-related">
  <h3>関連する無料ツール</h3>
  <ul>
    <li><a href="/ja/tools/meta-tag-generator/">メタタグジェネレーター</a></li>
    <li><a href="/ja/tools/privacy-policy-generator/">プライバシーポリシージェネレーター</a></li>
    <li><a href="/ja/tools/html-table-generator/">HTMLテーブルジェネレーター</a></li>
  </ul>
</div>

<!-- ── freee CTA ── -->
<div class="sa-freee-cta">
  <div class="sa-freee-cta-text">
    <strong>freee で請求書・経費管理もスマートに</strong>
    <p>メール署名が整ったら、次は業務効率化。freee の無料プランで請求書作成・経費精算・確定申告をまとめて管理できます。</p>
  </div>
  <a href="https://www.freee.co.jp/" class="sa-freee-cta-btn" target="_blank" rel="noopener">freee を無料で試す</a>
</div>

<script>
(function () {
  /* ── 状態管理 ── */
  var state = {
    tpl: 'corporate',
    color: '#6366f1'
  };

  /* ── テンプレート定義 ── */
  var TPL = {
    corporate: function (d, color, font, sep, layout, photo) {
      var photoHtml = saPhotoHtml(photo, color, 64);
      var sepHtml = sep !== 'none'
        ? '<tr><td colspan="2" style="padding:8px 0"><hr style="border:none;border-top:1px ' + sep + ' ' + color + ';margin:0"></td></tr>'
        : '';
      if (layout === 'horizontal') {
        return '<table cellpadding="0" cellspacing="0" style="font-family:' + font + ';font-size:13px;color:#1a1a1a">'
          + sepHtml
          + '<tr>'
          + (photo !== 'none' ? '<td style="padding-right:14px;vertical-align:top">' + photoHtml + '</td>' : '')
          + '<td style="vertical-align:top">'
          + (d.name ? '<div style="font-size:15px;font-weight:700;color:' + color + '">' + saEsc(d.name) + '</div>' : '')
          + (d.title ? '<div style="font-size:12px;color:#475569">' + saEsc(d.title) + '</div>' : '')
          + (d.company ? '<div style="font-size:12px;font-weight:600">' + saEsc(d.company) + '</div>' : '')
          + '<div style="margin-top:6px;font-size:12px;color:#475569">'
          + (d.phone ? '&#128222; ' + saEsc(d.phone) + '&nbsp;&nbsp;' : '')
          + (d.email ? '<a href="mailto:' + saEsc(d.email) + '" style="color:' + color + ';text-decoration:none">&#9993; ' + saEsc(d.email) + '</a>&nbsp;&nbsp;' : '')
          + (d.website ? '<a href="' + saEsc(d.website) + '" style="color:' + color + ';text-decoration:none">&#127758; ' + saEsc(d.website) + '</a>' : '')
          + '</div>'
          + saSocialRow(d, color)
          + '</td>'
          + '</tr>'
          + '</table>';
      } else {
        return '<table cellpadding="0" cellspacing="0" style="font-family:' + font + ';font-size:13px;color:#1a1a1a;text-align:center">'
          + sepHtml
          + (photo !== 'none' ? '<tr><td style="padding-bottom:8px">' + photoHtml + '</td></tr>' : '')
          + '<tr><td><div style="font-size:15px;font-weight:700;color:' + color + '">' + (d.name ? saEsc(d.name) : 'お名前') + '</div></td></tr>'
          + (d.title ? '<tr><td><div style="font-size:12px;color:#475569">' + saEsc(d.title) + '</div></td></tr>' : '')
          + (d.company ? '<tr><td><div style="font-size:12px;font-weight:600">' + saEsc(d.company) + '</div></td></tr>' : '')
          + '<tr><td style="padding-top:6px;font-size:12px;color:#475569">'
          + (d.phone ? '&#128222; ' + saEsc(d.phone) + '<br>' : '')
          + (d.email ? '<a href="mailto:' + saEsc(d.email) + '" style="color:' + color + ';text-decoration:none">&#9993; ' + saEsc(d.email) + '</a><br>' : '')
          + (d.website ? '<a href="' + saEsc(d.website) + '" style="color:' + color + ';text-decoration:none">&#127758; ' + saEsc(d.website) + '</a>' : '')
          + '</td></tr>'
          + saSocialRow(d, color)
          + '</table>';
      }
    },

    creative: function (d, color, font, sep, layout, photo) {
      var photoHtml = saPhotoHtml(photo, color, 70);
      var sepLine = sep !== 'none'
        ? '<tr><td colspan="2"><div style="width:40px;height:4px;background:' + color + ';border-radius:2px;margin-bottom:10px"></div></td></tr>'
        : '';
      return '<table cellpadding="0" cellspacing="0" style="font-family:' + font + ';font-size:13px;color:#1a1a1a">'
        + sepLine
        + '<tr>'
        + (photo !== 'none' && layout === 'horizontal' ? '<td style="padding-right:16px;vertical-align:top">' + photoHtml + '</td>' : '')
        + '<td style="vertical-align:top;border-left:4px solid ' + color + ';padding-left:12px">'
        + (d.name ? '<div style="font-size:16px;font-weight:900;letter-spacing:-.5px;color:' + color + '">' + saEsc(d.name) + '</div>' : '')
        + (d.title ? '<div style="font-size:11px;text-transform:uppercase;letter-spacing:.1em;color:#64748b;margin-bottom:4px">' + saEsc(d.title) + '</div>' : '')
        + (d.company ? '<div style="font-size:12px;font-weight:700">' + saEsc(d.company) + '</div>' : '')
        + '<div style="margin-top:8px;font-size:12px">'
        + (d.phone ? '<span style="color:#64748b">&#128222; ' + saEsc(d.phone) + '</span><br>' : '')
        + (d.email ? '<a href="mailto:' + saEsc(d.email) + '" style="color:' + color + ';text-decoration:none;font-weight:600">&#9993; ' + saEsc(d.email) + '</a><br>' : '')
        + (d.website ? '<a href="' + saEsc(d.website) + '" style="color:' + color + ';text-decoration:none">&#127758; ' + saEsc(d.website) + '</a>' : '')
        + '</div>'
        + saSocialRow(d, color)
        + '</td>'
        + '</tr>'
        + '</table>';
    },

    minimal: function (d, color, font, sep, layout, photo) {
      var sepHtml = sep !== 'none'
        ? '<div style="border-top:1px ' + sep + ' #cbd5e1;margin-bottom:8px"></div>'
        : '';
      return '<div style="font-family:' + font + ';font-size:13px;color:#334155;line-height:1.7">'
        + sepHtml
        + (d.name ? '<span style="font-weight:700;color:#0f172a">' + saEsc(d.name) + '</span>' : '')
        + (d.title ? ' &middot; <span style="color:#64748b">' + saEsc(d.title) + '</span>' : '')
        + (d.company ? (d.name || d.title ? '、' : '') + '<span style="color:#64748b">' + saEsc(d.company) + '</span>' : '')
        + '<br>'
        + (d.phone ? saEsc(d.phone) + ' &bull; ' : '')
        + (d.email ? '<a href="mailto:' + saEsc(d.email) + '" style="color:' + color + ';text-decoration:none">' + saEsc(d.email) + '</a>' : '')
        + (d.website ? ' &bull; <a href="' + saEsc(d.website) + '" style="color:' + color + ';text-decoration:none">' + saEsc(d.website) + '</a>' : '')
        + saSocialRowInline(d, color)
        + '</div>';
    },

    developer: function (d, color, font, sep, layout, photo) {
      var monoFont = "'Courier New', Courier, monospace";
      var sepHtml = sep !== 'none'
        ? '<div style="border-top:1px ' + sep + ' ' + color + ';margin-bottom:10px"></div>'
        : '';
      return '<div style="font-family:' + monoFont + ';font-size:12px;color:#e2e8f0;background:#0f172a;padding:14px 16px;border-radius:8px;line-height:1.8">'
        + sepHtml
        + '<span style="color:#7dd3fc">const</span> <span style="color:#bfdbfe">signature</span> <span style="color:#94a3b8">= {</span><br>'
        + (d.name ? '&nbsp;&nbsp;<span style="color:#6ee7b7">name</span><span style="color:#94a3b8">:</span> <span style="color:#fde68a">"' + saEsc(d.name) + '"</span>,<br>' : '')
        + (d.title ? '&nbsp;&nbsp;<span style="color:#6ee7b7">title</span><span style="color:#94a3b8">:</span> <span style="color:#fde68a">"' + saEsc(d.title) + '"</span>,<br>' : '')
        + (d.company ? '&nbsp;&nbsp;<span style="color:#6ee7b7">company</span><span style="color:#94a3b8">:</span> <span style="color:#fde68a">"' + saEsc(d.company) + '"</span>,<br>' : '')
        + (d.email ? '&nbsp;&nbsp;<span style="color:#6ee7b7">email</span><span style="color:#94a3b8">:</span> <a href="mailto:' + saEsc(d.email) + '" style="color:#93c5fd;text-decoration:none">"' + saEsc(d.email) + '"</a>,<br>' : '')
        + (d.github ? '&nbsp;&nbsp;<span style="color:#6ee7b7">github</span><span style="color:#94a3b8">:</span> <a href="https://github.com/' + saEsc(d.github) + '" style="color:#93c5fd;text-decoration:none">"github.com/' + saEsc(d.github) + '"</a>,<br>' : '')
        + (d.website ? '&nbsp;&nbsp;<span style="color:#6ee7b7">web</span><span style="color:#94a3b8">:</span> <a href="' + saEsc(d.website) + '" style="color:#93c5fd;text-decoration:none">"' + saEsc(d.website) + '"</a>,<br>' : '')
        + '<span style="color:#94a3b8">};</span>'
        + '</div>';
    }
  };

  /* ── ヘルパー関数 ── */
  function saEsc(s) {
    return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  function saPhotoHtml(type, color, size) {
    if (type === 'none') return '';
    var radius = type === 'circle' ? '50%' : '8px';
    return '<div style="width:' + size + 'px;height:' + size + 'px;border-radius:' + radius + ';background:' + color + ';display:flex;align-items:center;justify-content:center;font-size:' + Math.floor(size*0.45) + 'px;color:#fff;font-weight:700;line-height:1">&#128100;</div>';
  }

  function saSocialRow(d, color) {
    var links = [];
    if (d.linkedin) links.push('<a href="' + saEsc(d.linkedin) + '" style="color:' + color + ';text-decoration:none;font-size:12px;font-weight:600">LinkedIn</a>');
    if (d.twitter) links.push('<a href="https://twitter.com/' + saEsc(d.twitter.replace('@','')) + '" style="color:' + color + ';text-decoration:none;font-size:12px;font-weight:600">Twitter/X</a>');
    if (d.github) links.push('<a href="https://github.com/' + saEsc(d.github) + '" style="color:' + color + ';text-decoration:none;font-size:12px;font-weight:600">GitHub</a>');
    if (!links.length) return '';
    return '<tr><td colspan="2" style="padding-top:6px">' + links.join(' &nbsp;·&nbsp; ') + '</td></tr>';
  }

  function saSocialRowInline(d, color) {
    var links = [];
    if (d.linkedin) links.push('<a href="' + saEsc(d.linkedin) + '" style="color:' + color + ';text-decoration:none">LinkedIn</a>');
    if (d.twitter) links.push('<a href="https://twitter.com/' + saEsc(d.twitter.replace('@','')) + '" style="color:' + color + ';text-decoration:none">Twitter/X</a>');
    if (d.github) links.push('<a href="https://github.com/' + saEsc(d.github) + '" style="color:' + color + ';text-decoration:none">GitHub</a>');
    if (!links.length) return '';
    return '<br>' + links.join(' &nbsp;·&nbsp; ');
  }

  function saGetData() {
    return {
      name:     document.getElementById('sa-name').value.trim(),
      title:    document.getElementById('sa-title').value.trim(),
      company:  document.getElementById('sa-company').value.trim(),
      phone:    document.getElementById('sa-phone').value.trim(),
      email:    document.getElementById('sa-email').value.trim(),
      website:  document.getElementById('sa-website').value.trim(),
      linkedin: document.getElementById('sa-linkedin').value.trim(),
      twitter:  document.getElementById('sa-twitter').value.trim(),
      github:   document.getElementById('sa-github').value.trim()
    };
  }

  /* ── 公開関数 ── */
  window.saRender = function () {
    var d = saGetData();
    var color = state.color;
    var font  = document.getElementById('sa-font').value;
    var sep   = document.getElementById('sa-sep').value;
    var layout= document.getElementById('sa-layout').value;
    var photo = document.getElementById('sa-photo').value;
    var html  = TPL[state.tpl](d, color, font, sep, layout, photo);
    document.getElementById('sa-preview').innerHTML = html;
    var out = document.getElementById('sa-html-out');
    out.value = html;
  };

  window.saSetTpl = function (name, btn) {
    state.tpl = name;
    document.querySelectorAll('#sig-app .sa-tpl-btn').forEach(function(b){ b.classList.remove('active'); });
    btn.classList.add('active');
    saRender();
  };

  window.saPick = function (el) {
    state.color = el.dataset.color;
    document.querySelectorAll('#sig-app .sa-swatch').forEach(function(s){ s.classList.remove('active'); });
    el.classList.add('active');
    saRender();
  };

  window.saCopyHTML = function () {
    var d = saGetData();
    var color = state.color;
    var font  = document.getElementById('sa-font').value;
    var sep   = document.getElementById('sa-sep').value;
    var layout= document.getElementById('sa-layout').value;
    var photo = document.getElementById('sa-photo').value;
    var html  = TPL[state.tpl](d, color, font, sep, layout, photo);
    navigator.clipboard.writeText(html).then(function () {
      var t = document.getElementById('sa-toast');
      t.classList.add('show');
      setTimeout(function(){ t.classList.remove('show'); }, 2500);
    });
  };

  window.saToggleCode = function () {
    var out = document.getElementById('sa-html-out');
    out.style.display = out.style.display === 'block' ? 'none' : 'block';
  };

  window.saReset = function () {
    ['sa-name','sa-title','sa-company','sa-phone','sa-email','sa-website','sa-linkedin','sa-twitter','sa-github'].forEach(function(id){
      document.getElementById(id).value = '';
    });
    document.getElementById('sa-layout').value = 'horizontal';
    document.getElementById('sa-font').value = 'Arial, Helvetica, sans-serif';
    document.getElementById('sa-sep').value = 'solid';
    document.getElementById('sa-photo').value = 'circle';
    state.color = '#6366f1';
    document.querySelectorAll('#sig-app .sa-swatch').forEach(function(s){ s.classList.remove('active'); });
    document.querySelector('#sig-app .sa-swatch').classList.add('active');
    saRender();
  };

  /* ── 初期化 ── */
  saRender();
})();
</script>
</div>

---

## メール署名をより効果的にするコツ

**情報は簡潔に。** 4〜6行を目安にしましょう。情報が多すぎると読まれにくくなり、かえって印象が薄れます。

**メール安全フォントを使う。** このツールはArial・Georgia・Verdanaなどのウェブセーフフォントをデフォルトとしており、外部フォントの読み込みなしにあらゆるメールクライアントで正しく表示されます。

**画像は控えめに。** 多くのメールクライアントはデフォルトで画像をブロックします。ロゴを使う場合は安定したURLにホストした `<img>` タグを利用してください。生成されたHTMLに手動で追加するのが最も確実です。

**送信前にテスト。** 署名を設定したら、まず自分宛にテストメールを送り、モバイルとデスクトップ両方で表示を確認しましょう。

**定期的に更新。** 役職や連絡先が変わった際は忘れずに署名も更新してください。常に正確な情報を相手に届けることが信頼の基本です。

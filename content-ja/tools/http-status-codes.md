---
title: "HTTPステータスコード一覧 — クイックリファレンス"
date: 2026-01-13
description: "HTTPステータスコード完全リファレンス。説明・使用例・カラーコード付き検索可能リスト。1xx〜5xxステータスコードを即座に検索。"
categories: ["無料ツール"]
slug: "http-status-codes"
ShowToc: false
aliases:
  - "/ja/tools/http-status-codes/"
  - "/ja/tools/http-status-codes/"
cover:
  image: "/images/covers/http-status-codes-ja.png"
  alt: "HTTPステータスコード一覧"
---

<div id="http-app">

<style>
#http-app {
font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Noto Sans JP", "Segoe UI", sans-serif;
max-width: 900px;
margin: 0 auto;
padding: 0 16px 48px;
color: #1a1a2e;
}

/* ── コントロール ── */
#http-app .hsc-controls {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-bottom: 24px;
}

#http-app .hsc-search {
flex: 1 1 220px;
padding: 10px 14px;
border: 2px solid #d1d5db;
border-radius: 8px;
font-size: 15px;
outline: none;
transition: border-color 0.2s;
}
#http-app .hsc-search:focus {
border-color: #4f46e5;
}

#http-app .hsc-filter-group {
display: flex;
flex-wrap: wrap;
gap: 6px;
}

#http-app .hsc-filter-btn {
padding: 8px 14px;
border: 2px solid transparent;
border-radius: 20px;
font-size: 13px;
font-weight: 700;
cursor: pointer;
transition: all 0.18s;
background: #f3f4f6;
color: #374151;
}
#http-app .hsc-filter-btn:hover,
#http-app .hsc-filter-btn.active {
color: #fff;
}
#http-app .hsc-filter-btn[data-cat="all"].active  { background: #4f46e5; }
#http-app .hsc-filter-btn[data-cat="1xx"].active  { background: #6366f1; }
#http-app .hsc-filter-btn[data-cat="2xx"].active  { background: #16a34a; }
#http-app .hsc-filter-btn[data-cat="3xx"].active  { background: #d97706; }
#http-app .hsc-filter-btn[data-cat="4xx"].active  { background: #dc2626; }
#http-app .hsc-filter-btn[data-cat="5xx"].active  { background: #7c3aed; }

/* ── 件数 ── */
#http-app .hsc-count {
font-size: 13px;
color: #6b7280;
margin-bottom: 16px;
}

/* ── カテゴリ見出し ── */
#http-app .hsc-cat-heading {
display: flex;
align-items: center;
gap: 10px;
margin: 28px 0 10px;
font-size: 18px;
font-weight: 700;
}
#http-app .hsc-cat-badge {
display: inline-block;
padding: 3px 12px;
border-radius: 12px;
font-size: 13px;
font-weight: 700;
color: #fff;
}
#http-app .hsc-cat-badge.c1xx { background: #6366f1; }
#http-app .hsc-cat-badge.c2xx { background: #16a34a; }
#http-app .hsc-cat-badge.c3xx { background: #d97706; }
#http-app .hsc-cat-badge.c4xx { background: #dc2626; }
#http-app .hsc-cat-badge.c5xx { background: #7c3aed; }

/* ── カード ── */
#http-app .hsc-card {
border-radius: 10px;
border: 1.5px solid #e5e7eb;
margin-bottom: 8px;
overflow: hidden;
transition: box-shadow 0.18s;
}
#http-app .hsc-card:hover {
box-shadow: 0 2px 10px rgba(0,0,0,0.09);
}
#http-app .hsc-card.common {
border-width: 2px;
}
#http-app .hsc-card.c1xx.common { border-color: #6366f1; }
#http-app .hsc-card.c2xx.common { border-color: #16a34a; }
#http-app .hsc-card.c3xx.common { border-color: #d97706; }
#http-app .hsc-card.c4xx.common { border-color: #dc2626; }
#http-app .hsc-card.c5xx.common { border-color: #7c3aed; }

#http-app .hsc-card-header {
display: flex;
align-items: center;
gap: 12px;
padding: 12px 16px;
cursor: pointer;
user-select: none;
background: #fff;
}
#http-app .hsc-card-header:hover {
background: #f9fafb;
}

#http-app .hsc-code-num {
font-size: 20px;
font-weight: 800;
min-width: 56px;
text-align: center;
padding: 4px 8px;
border-radius: 6px;
color: #fff;
letter-spacing: -0.5px;
flex-shrink: 0;
}
#http-app .hsc-code-num.c1xx { background: #6366f1; }
#http-app .hsc-code-num.c2xx { background: #16a34a; }
#http-app .hsc-code-num.c3xx { background: #d97706; }
#http-app .hsc-code-num.c4xx { background: #dc2626; }
#http-app .hsc-code-num.c5xx { background: #7c3aed; }

#http-app .hsc-card-meta {
flex: 1;
min-width: 0;
}
#http-app .hsc-code-name {
font-size: 15px;
font-weight: 700;
color: #111827;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
}
#http-app .hsc-code-desc {
font-size: 13px;
color: #6b7280;
margin-top: 2px;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
}

#http-app .hsc-common-star {
font-size: 11px;
font-weight: 700;
color: #fff;
background: #f59e0b;
padding: 2px 7px;
border-radius: 10px;
white-space: nowrap;
flex-shrink: 0;
}

#http-app .hsc-copy-btn {
flex-shrink: 0;
padding: 6px 12px;
border: 1.5px solid #d1d5db;
border-radius: 6px;
font-size: 12px;
font-weight: 700;
background: #fff;
color: #374151;
cursor: pointer;
transition: all 0.15s;
}
#http-app .hsc-copy-btn:hover {
background: #4f46e5;
color: #fff;
border-color: #4f46e5;
}
#http-app .hsc-copy-btn.copied {
background: #16a34a;
color: #fff;
border-color: #16a34a;
}

#http-app .hsc-chevron {
flex-shrink: 0;
width: 20px;
height: 20px;
color: #9ca3af;
transition: transform 0.2s;
}
#http-app .hsc-card.open .hsc-chevron {
transform: rotate(180deg);
}

/* ── 詳細パネル ── */
#http-app .hsc-detail {
display: none;
padding: 14px 20px 18px;
border-top: 1px solid #e5e7eb;
background: #f9fafb;
font-size: 14px;
line-height: 1.8;
color: #374151;
}
#http-app .hsc-card.open .hsc-detail {
display: block;
}

#http-app .hsc-detail h4 {
margin: 0 0 6px;
font-size: 12px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.07em;
color: #6b7280;
}
#http-app .hsc-detail p {
margin: 0 0 12px;
}
#http-app .hsc-detail .hsc-usecase {
background: #fff;
border: 1px solid #e5e7eb;
border-radius: 6px;
padding: 10px 14px;
font-size: 13px;
color: #374151;
}

/* ── 検索結果なし ── */
#http-app .hsc-no-results {
text-align: center;
padding: 48px 0;
color: #9ca3af;
font-size: 16px;
display: none;
}

/* ── freee CTA ── */
#http-app .hsc-freee-cta {
margin-top: 48px;
padding: 24px 28px;
background: linear-gradient(135deg, #e0f2fe 0%, #ede9fe 100%);
border: 1.5px solid #bfdbfe;
border-radius: 14px;
text-align: center;
}
#http-app .hsc-freee-cta h3 {
font-size: 18px;
font-weight: 800;
margin: 0 0 8px;
color: #1e3a5f;
}
#http-app .hsc-freee-cta p {
font-size: 14px;
color: #374151;
margin: 0 0 16px;
line-height: 1.7;
}
#http-app .hsc-freee-cta a {
display: inline-block;
padding: 11px 28px;
background: #4f46e5;
color: #fff;
font-weight: 700;
font-size: 15px;
border-radius: 8px;
text-decoration: none;
transition: background 0.18s;
}
#http-app .hsc-freee-cta a:hover {
background: #3730a3;
}

/* ── モバイル ── */
@media (max-width: 600px) {
#http-app .hsc-code-desc { display: none; }
#http-app .hsc-copy-btn { display: none; }
#http-app .hsc-freee-cta { padding: 18px 16px; }
}
</style>

<!-- コントロール -->
<div class="hsc-controls">
<input
id="hscSearch"
class="hsc-search"
type="search"
placeholder="コード番号またはキーワードで検索… 例: 404 または not found"
aria-label="HTTPステータスコードを検索"
/>
<div class="hsc-filter-group" role="group" aria-label="カテゴリで絞り込み">
<button class="hsc-filter-btn active" data-cat="all">すべて</button>
<button class="hsc-filter-btn" data-cat="1xx">1xx 情報</button>
<button class="hsc-filter-btn" data-cat="2xx">2xx 成功</button>
<button class="hsc-filter-btn" data-cat="3xx">3xx リダイレクト</button>
<button class="hsc-filter-btn" data-cat="4xx">4xx クライアントエラー</button>
<button class="hsc-filter-btn" data-cat="5xx">5xx サーバーエラー</button>
</div>
</div>

<div id="hscCount" class="hsc-count"></div>

<!-- JSによってレンダリングされるコードリスト -->
<div id="hscList"></div>
<div id="hscNoResults" class="hsc-no-results">条件に一致するステータスコードが見つかりません。</div>

<script>
(function () {
var COMMON = [200,201,301,302,400,401,403,404,500,502,503];

var CODES = [
/* ── 1xx ── */
{
code: 100, name: "Continue（継続）",
desc: "リクエストヘッダーを受信。クライアントは続行できます。",
detail: "サーバーがリクエストの最初の部分を受信し、クライアントが処理を続行してよいことを示す暫定レスポンスです。クライアントがすでにリクエストを完了している場合は無視してください。",
usecase: "クライアントが大きなリクエストボディを送信する前に Expect: 100-continue ヘッダーを送信するケース。サーバーが 100 を返すことでボディ受信準備完了を通知します。"
},
{
code: 101, name: "Switching Protocols（プロトコル切り替え）",
desc: "サーバーがプロトコルの切り替えに同意しました。",
detail: "クライアントからの Upgrade リクエストヘッダーに応答して送信され、サーバーが切り替えるプロトコルを示します。このレスポンスの空白行の直後にプロトコルが切り替わります。",
usecase: "HTTP 接続を WebSocket へアップグレードする場合（Upgrade: websocket ヘッダー）。サーバーは 101 を返してプロトコル切り替えを確認します。"
},
{
code: 102, name: "Processing（処理中）",
desc: "サーバーはリクエストを受信し処理中ですが、まだレスポンスはありません。",
detail: "WebDAV のレスポンスコードで、サーバーがリクエストを受信して処理中であるが、まだ使用可能なレスポンスがないことを示します。長時間処理中にクライアントがタイムアウトするのを防ぎます。",
usecase: "完了まで数秒以上かかる WebDAV 操作で、クライアントのタイムアウトを防ぐために使用します。"
},
{
code: 103, name: "Early Hints（早期ヒント）",
desc: "最終レスポンスの前に一部のレスポンスヘッダーを返します。",
detail: "サーバーが最終 HTTP メッセージの前に予備 HTTP ヘッダーを送信できるようにします。主に Link ヘッダーと組み合わせて、サーバーがレスポンスを準備している間にブラウザーがリソースをプリロードできるようにします。",
usecase: "メイン HTML レスポンスを生成しながら CSS/JS ファイルの Link ヘッダーを送信し、ブラウザーがアセットの先読みを早めに開始できるようにします。"
},
/* ── 2xx ── */
{
code: 200, name: "OK（成功）",
desc: "リクエストが成功しました。",
detail: "HTTP リクエスト成功に対する標準レスポンスです。実際のレスポンスはリクエストメソッドによって異なります。GET はリソースを返し、POST はアクションの結果を返し、HEAD はヘッダーのみを返します。Web 上で最も一般的なレスポンスコードです。",
usecase: "GET・POST・PUT・PATCH リクエストの標準成功レスポンス。ユーザーデータを返す API やページが正常に読み込まれる場合。"
},
{
code: 201, name: "Created（作成済み）",
desc: "リクエストが成功し、新しいリソースが作成されました。",
detail: "リクエストが成功し、その結果として新しいリソースが作成されたことを示します。レスポンスには通常、新規作成されたリソースを指す Location ヘッダーが含まれ、レスポンスボディには新リソースの表現が含まれることがあります。",
usecase: "POST /users で新しいユーザーを作成した後の REST API レスポンス。Location ヘッダーは /users/123 を指します。"
},
{
code: 202, name: "Accepted（受付済み）",
desc: "リクエストは受信されましたが、まだ処理されていません。",
detail: "リクエストは処理のために受け付けられましたが、処理はまだ完了していないことを示します。リクエストが最終的に処理されるかどうかは保証されません。通常、非同期操作に使用されます。",
usecase: "動画エンコードジョブの送信: サーバーはすぐにリクエストを受け付けますが、エンコードはバックグラウンドで行われます。"
},
{
code: 203, name: "Non-Authoritative Information（信頼できない情報）",
desc: "返されたメタデータはオリジンサーバーからのものではありません。",
detail: "返されたメタデータは、オリジンサーバーから利用可能なものと完全に同じではなく、ローカルまたはサードパーティのコピーから収集されたものです。主にミラーやバックアップで使用されます。",
usecase: "プロキシサーバーがオリジンと若干異なるキャッシュコピーから変更されたヘッダーまたはコンテンツを返す場合。"
},
{
code: 204, name: "No Content（コンテンツなし）",
desc: "レスポンスボディに送信するコンテンツはありません。",
detail: "リクエストは成功しましたが、クライアントは現在のページから離れる必要がないことを示します。DELETE リクエストの後や、レスポンスにボディが必要ない PUT/PATCH での更新時によく使用されます。",
usecase: "DELETE /items/42 が成功 — サーバーはボディなしで 204 を返します。UI を更新する必要がない自動保存操作にも使用されます。"
},
{
code: 205, name: "Reset Content（コンテンツリセット）",
desc: "このリクエストを送信したドキュメントビューをリセットしてください。",
detail: "リクエストを送信したドキュメントをリセットするようクライアントに指示します。204 No Content に似ていますが、フォーム送信後にフォームフィールドをクリアするなど、ドキュメントビューのリセットが必要です。",
usecase: "フォーム送信後、ユーザーが新しいデータを入力できるようにブラウザーにフォームフィールドをクリアするよう指示します。"
},
{
code: 206, name: "Partial Content（部分的コンテンツ）",
desc: "範囲リクエストにより部分的なコンテンツが配信されました。",
detail: "クライアントがリソースの一部のみを要求する Range ヘッダーを送信した場合に使用されます。レスポンスには配信された範囲を示す Content-Range ヘッダーが含まれている必要があります。再開可能なダウンロードや動画ストリーミングを可能にします。",
usecase: "動画ストリーミング: プレーヤーが Range: bytes=0-1048575 で先頭チャンクを要求。サーバーはそのチャンクで 206 を返します。"
},
{
code: 207, name: "Multi-Status（マルチステータス）",
desc: "複数リソースに関する情報を伝達します（WebDAV）。",
detail: "複数のステータスコードが適切な状況で、複数のリソースに関する情報を伝達する WebDAV レスポンスです。レスポンスボディは各リソースの個別ステータスコードを含む XML ドキュメントです。",
usecase: "WebDAV PROPFIND または COPY 操作で複数のリソースに影響し、それぞれ独自の成功/失敗ステータスを持つ場合。"
},
{
code: 208, name: "Already Reported（既に報告済み）",
desc: "DAV バインディングのメンバーはすでに列挙されています（WebDAV）。",
detail: "同じコレクションへの複数バインディングの内部メンバーを繰り返し列挙することを避けるため、DAV: propstat レスポンス要素内で使用されます。",
usecase: "WebDAV: コレクションに循環参照が含まれる場合の無限ループ防止。"
},
{
code: 226, name: "IM Used（IM 使用済み）",
desc: "サーバーはデルタエンコーディングを使用して GET リクエストを処理しました。",
detail: "サーバーはリソースへの GET リクエストを処理し、レスポンスは現在のインスタンスに適用された 1 つ以上のインスタンス操作の結果を表します。HTTP デルタエンコーディングで使用されます。",
usecase: "デルタエンコーディング: サーバーは以前キャッシュされたリソースバージョンからの変更（差分）のみを送信します。"
},
/* ── 3xx ── */
{
code: 300, name: "Multiple Choices（複数の選択肢）",
desc: "リクエストには複数の可能なレスポンスがあります。",
detail: "リクエストに対して複数の可能なレスポンスがあることを示します。ユーザーエージェントまたはユーザーはそのいずれかを選択する必要があります。自動的に選択する標準化された方法はありませんが、サーバーは優先される選択肢を示すことができます。",
usecase: "複数のフォーマット（HTML、JSON、XML）で利用可能なリソース — サーバーが選択肢を提示し、クライアントが 1 つを選びます。"
},
{
code: 301, name: "Moved Permanently（恒久移動）",
desc: "リクエストされたリソースの URL は永久に変更されました。",
detail: "リソースが新しい URL に恒久的に移動したことを示します。検索エンジンはリンクを新しい URL に更新します。ブラウザーはこのリダイレクトをキャッシュします。新しい URL は Location ヘッダーで提供されます。GET メソッドはリダイレクト後も GET に変更される場合があります。",
usecase: "HTTP から HTTPS へのリダイレクト、またはウェブサイトのドメイン変更。古い URL の SEO 価値が新しい URL に引き継がれます。"
},
{
code: 302, name: "Found（一時移動）",
desc: "URL は一時的に変更されています。",
detail: "リソースが一時的に別の URI で見つかることを示します。クライアントは元の URI を引き続き使用する必要があります。ブラウザーはリダイレクトを追いますが、恒久的にキャッシュしません。メソッドを変更してはならない場合は 307 が推奨されます。",
usecase: "Post/Redirect/Get パターン: フォーム POST が成功した後、ブラウザーを結果ページにリダイレクトして、更新時にフォームが再送信されないようにします。"
},
{
code: 303, name: "See Other（別のページを参照）",
desc: "常に GET を使用して別のページにリダイレクトします。",
detail: "リダイレクトが要求されたリソース自体ではなく、別のページ（確認ページなど）にリンクしていることを示します。302 とは異なり、元のメソッドに関係なく新しい URL への GET を常にトリガーします。",
usecase: "POST フォーム送信でリソースが作成された後、新しいリソースを表示する GET ページにブラウザーをリダイレクトします。"
},
{
code: 304, name: "Not Modified（未更新）",
desc: "レスポンスが変更されていないことをクライアントに伝えます。",
detail: "キャッシュに使用されます。レスポンスが変更されていないため、クライアントはすでに持っているキャッシュ版を使用できることを示します。レスポンスにボディを含めてはいけません。If-None-Match または If-Modified-Since を使用した条件付きリクエストによってトリガーされます。",
usecase: "ブラウザーが ETag 付きで If-None-Match: \"abc123\" を送信。サーバーはリソースが変更されていないことを確認 — クライアントはキャッシュを使用します。"
},
{
code: 307, name: "Temporary Redirect（一時リダイレクト）",
desc: "一時的なリダイレクト。メソッドは変更してはなりません。",
detail: "302 Found に似ていますが、リダイレクトされたリクエストが行われる際にメソッドとボディが変更されないことを保証します。POST がリダイレクトされた場合、新しいリクエストも POST になります。HTTP メソッドを保持する必要がある場合に使用します。",
usecase: "メンテナンス中に POST メソッドを保持しながら API POST エンドポイントを別のサーバーに一時的にルーティングします。"
},
{
code: 308, name: "Permanent Redirect（恒久リダイレクト）",
desc: "恒久的なリダイレクト。メソッドは変更してはなりません。",
detail: "301 Moved Permanently に似ていますが、メソッドとボディが変更されないことを保証します。検索エンジンはリンクを更新し、ブラウザーは恒久的にキャッシュし、HTTP メソッドは保持されます。307 の恒久版です。",
usecase: "クライアントが依然として POST（GET ではなく）を送信することを保証しながら、API エンドポイントを /v1/users から /v2/users に恒久移動します。"
},
/* ── 4xx ── */
{
code: 400, name: "Bad Request（不正なリクエスト）",
desc: "クライアントエラーのためサーバーはリクエストを処理できません。",
detail: "クライアント側のエラー（不正なリクエスト構文、無効なリクエストメッセージのフレーミング、または欺くようなリクエストルーティング）と思われるため、サーバーはリクエストを処理できないか処理しません。クライアントは変更なしにリクエストを繰り返すべきではありません。",
usecase: "API リクエストボディの必須フィールド欠落、不正な JSON、無効なクエリパラメーターの型。"
},
{
code: 401, name: "Unauthorized（認証が必要）",
desc: "認証が必要ですが、提供されていません。",
detail: "'Unauthorized（未認可）'という名前ですが、実際には「未認証」を意味します。クライアントはリクエストされたレスポンスを得るために自身を認証する必要があります。レスポンスにはリクエストされたリソースに適用可能なチャレンジを含む WWW-Authenticate ヘッダーを含める必要があります。",
usecase: "Authorization ヘッダーなしや無効/期限切れのトークンで保護された API エンドポイントにアクセスする場合。"
},
{
code: 402, name: "Payment Required（支払いが必要）",
desc: "将来の使用のために予約済み。レート制限に使用されることもあります。",
detail: "もともとデジタル決済システム向けに意図されていました。仕様が曖昧で、ほとんど使用されません。一部の API では、無料ティアのクォータを超えてサブスクリプションが必要な場合に使用します。",
usecase: "一部の SaaS API は無料ティアのクォータを超えた際に 402 を返し、有料プランが必要であることを示します。"
},
{
code: 403, name: "Forbidden（アクセス禁止）",
desc: "サーバーはリクエストを承認することを拒否します。",
detail: "クライアントの身元は判明していますが、コンテンツへのアクセス権がありません。401 とは異なり、再認証しても違いはありません。サーバーはリクエストを理解しましたが、認可を拒否します。",
usecase: "ログインしているユーザーが管理者専用ページにアクセスしようとする場合。または別のユーザーのプライベートデータにアクセスする場合。"
},
{
code: 404, name: "Not Found（見つかりません）",
desc: "サーバーはリクエストされたリソースを見つけられません。",
detail: "サーバーはリクエストされたリソースを見つけられません。これは URL が間違っている、リソースが存在したことがない、またはリソースが削除されたことを意味する場合があります。存在しないリソースのキャッチオールとしてよく使用されます。未認可クライアントからリソースの存在を隠すために 403 の代わりに 404 が返されることもあります。",
usecase: "削除されたブログ投稿、存在しないユーザー ID、または URL のタイプミスのリクエスト。"
},
{
code: 405, name: "Method Not Allowed（メソッドが許可されていません）",
desc: "リクエストメソッドはサポートされていません。",
detail: "リクエストメソッドはサーバーに認識されていますが、対象リソースではサポートされていません。サーバーはサポートされているメソッドを一覧表示する Allow ヘッダーを含める必要があります。",
usecase: "GET と POST のみをサポートするエンドポイントに DELETE リクエストを送信する場合。"
},
{
code: 406, name: "Not Acceptable（受け入れ不可）",
desc: "Accept ヘッダーに一致するコンテンツが見つかりませんでした。",
detail: "サーバーがリクエストで送信された Accept ヘッダーに一致するレスポンスを生成できないことを示します。例えば、クライアントが application/json のみを受け入れるが、サーバーが text/xml のみをサポートしている場合。",
usecase: "クライアントが Accept: application/json を送信するが、サーバーはそのリソースに対して XML のみを提供する場合。"
},
{
code: 407, name: "Proxy Authentication Required（プロキシ認証が必要）",
desc: "プロキシとの認証が必要です。",
detail: "401 と同様ですが、プロキシによる認証が必要です。プロキシはクライアントが認証するための Proxy-Authenticate ヘッダーを返す必要があります。",
usecase: "HTTP トラフィックが中間プロキシサーバーを通じて認証する必要がある企業環境。"
},
{
code: 408, name: "Request Timeout（リクエストタイムアウト）",
desc: "サーバーはリクエストの受信を待機中にタイムアウトしました。",
detail: "アイドル接続がシャットダウンされる際に一部のサーバーから送信されます。これはサーバーがこの未使用接続を閉じたいことを示します。Apache などの一部のサーバーで多く使用されます。",
usecase: "低速なクライアントがリクエストボディを送信するのに時間がかかりすぎた場合。サーバーはアイドルタイムアウト後に接続を閉じます。"
},
{
code: 409, name: "Conflict（競合）",
desc: "リクエストはリソースの現在の状態と競合しています。",
detail: "リクエストがサーバーの現在の状態と競合していることを示します。複数のリクエストがリソースを同時に編集している PUT リクエストで最も起こりやすいです。レスポンスボディは競合を説明する必要があります。",
usecase: "すでに存在するメールアドレスでユーザーを作成しようとする場合。または楽観的ロックシステムでのバージョン競合。"
},
{
code: 410, name: "Gone（削除済み）",
desc: "リソースは恒久的に削除され、戻ってきません。",
detail: "対象リソースへのアクセスが利用できなくなり、この状態が恒久的である可能性が高いことを示します。404 とは異なり、これは意図的な恒久削除を示します。検索エンジンに URL のインデックスを削除するよう通知するのに役立ちます。",
usecase: "廃止された製品。410 を送信することで、検索エンジンにインデックスから URL を削除するよう伝えます。"
},
{
code: 411, name: "Length Required（コンテンツ長が必要）",
desc: "Content-Length ヘッダーが必要です。",
detail: "サーバーは定義された Content-Length ヘッダーなしにリクエストを受け入れることを拒否します。クライアントは有効な Content-Length ヘッダーを追加すればリクエストを繰り返すことができます。",
usecase: "Content-Length ヘッダーを必要とするサーバーに、Content-Length ヘッダーなしで POST リクエストを送信する場合。"
},
{
code: 412, name: "Precondition Failed（前提条件の失敗）",
desc: "リソースへのアクセスが拒否されました。",
detail: "クライアントはサーバーが満たしていない前提条件をヘッダーに示しました。If-Match、If-None-Match、If-Modified-Since、If-Unmodified-Since ヘッダーを使用した条件付きリクエストで使用されます。",
usecase: "楽観的同時実行制御: クライアントがリソースを更新するために If-Match: \"old-etag\" を送信しますが、そのリソースはすでに他者によって変更されています。"
},
{
code: 413, name: "Content Too Large（コンテンツが大きすぎます）",
desc: "リクエストボディがサーバーの許容サイズを超えています。",
detail: "リクエストエンティティがサーバーで定義された制限より大きいです。サーバーは接続を閉じるか、状況が一時的であれば Retry-After ヘッダーを返すことがあります。",
usecase: "サーバーの最大許容アップロードサイズ（例: 10MB 超の画像）を超えるファイルのアップロード。"
},
{
code: 414, name: "URI Too Long（URI が長すぎます）",
desc: "リクエストされた URI がサーバーの処理可能な長さを超えています。",
detail: "提供された URI がサーバーが処理するには長すぎます。クライアントが長いクエリ文字列を持つ POST リクエストを GET リクエストに変換する場合に発生することがあります。",
usecase: "URL クエリ文字列に数千文字の検索クエリやフィルター。"
},
{
code: 415, name: "Unsupported Media Type（サポートされていないメディアタイプ）",
desc: "リクエストメディアタイプはサポートされていません。",
detail: "リクエストされたデータのメディアフォーマットがサーバーによってサポートされていないため、サーバーはリクエストを拒否しています。通常、Content-Type ヘッダーがサーバーの期待と一致しない場合にトリガーされます。",
usecase: "application/json のみを受け入れる API エンドポイントに text/plain を送信する場合。"
},
{
code: 416, name: "Range Not Satisfiable（範囲を満たせません）",
desc: "リクエストされた範囲を満たすことができません。",
detail: "リクエスト内の Range ヘッダーフィールドによって指定された範囲を満たすことができません。範囲が対象 URI のデータのサイズ外にある場合があります。レスポンスには実際のサイズを示すアスタリスク（*）を含む Content-Range ヘッダーが含まれます。",
usecase: "クライアントが 5000 バイトのファイルのバイト 9000-9999 をリクエストした場合 — 範囲がファイルの末尾を超えています。"
},
{
code: 417, name: "Expectation Failed（期待が失敗しました）",
desc: "Expect ヘッダーの期待を満たすことができません。",
detail: "Expect リクエストヘッダーフィールドによって示された期待をサーバーが満たすことができません。",
usecase: "クライアントが Expect: 100-continue を送信しますが、サーバーはその期待を満たすことができません（例: リクエストボディが大きすぎる）。"
},
{
code: 418, name: "I'm a Teapot（私はティーポットです）",
desc: "サーバーはティーポットなのでコーヒーを淹れることを拒否します。",
detail: "1998 年のエイプリルフールのジョークです（RFC 2324、Hyper Text Coffee Pot Control Protocol）。ティーポットでコーヒーを淹れようとする試みはこのエラーコードを返す必要があります。実際の HTTP サーバーによって実装されることは期待されていません。",
usecase: "API や開発者ツールのイースターエッグ。Google は https://www.google.com/teapot で 418 を返します。"
},
{
code: 422, name: "Unprocessable Content（処理できないコンテンツ）",
desc: "リクエストは整形式ですが意味的エラーがあります。",
detail: "サーバーはリクエストエンティティのコンテンツタイプを理解し、構文は正しいですが、含まれる指示を処理できませんでした。REST API でよく使用され、バリデーション失敗を示します — JSON は有効ですが、データがビジネスルールに違反しています。",
usecase: "有効な JSON ボディだがフィールドがバリデーションに失敗: age: -5 または email: 'メールではない'。"
},
{
code: 423, name: "Locked（ロック済み）",
desc: "アクセスされているリソースはロックされています（WebDAV）。",
detail: "アクセスされているリソースはロックされています。リソースがロックされて変更できない場合の WebDAV レスポンスです。",
usecase: "WebDAV: 別のユーザーがチェックアウトしているドキュメントは変更できません。"
},
{
code: 424, name: "Failed Dependency（依存関係の失敗）",
desc: "リクエストは失敗したリクエストに依存していたため失敗しました（WebDAV）。",
detail: "リクエストされたアクションが失敗した別のアクションに依存していたため、メソッドをリソースに対して実行できませんでした（WebDAV）。",
usecase: "WebDAV バッチ操作でバッチ内の先行操作が失敗した場合。"
},
{
code: 425, name: "Too Early（早すぎます）",
desc: "サーバーは再生される可能性のあるリクエストを処理するリスクを取りたくありません。",
detail: "サーバーが再生される可能性のあるリクエストを処理するリスクを取りたくないことを示します。TLS 早期データ（0-RTT）でのリプレイ攻撃を防ぐために使用されます。",
usecase: "TLS 1.3 早期データ: リプレイ攻撃を防ぐため、TLS ハンドシェイクで送信されたリクエストの処理をサーバーが拒否します。"
},
{
code: 426, name: "Upgrade Required（アップグレードが必要）",
desc: "クライアントは別のプロトコルに切り替える必要があります。",
detail: "サーバーは現在のプロトコルを使用してリクエストを実行することを拒否しますが、クライアントが別のプロトコルにアップグレードした後は実行する意思があります。サーバーは必要なプロトコルを示す Upgrade ヘッダーを含める必要があります。",
usecase: "サーバーがクライアントに HTTP/1.1 から HTTP/2 または HTTP から HTTPS へのアップグレードを要求する場合。"
},
{
code: 428, name: "Precondition Required（前提条件が必要）",
desc: "オリジンサーバーはリクエストを条件付きにすることを要求します。",
detail: "オリジンサーバーがリクエストを条件付きにすることを要求していることを示します。このレスポンスはクライアントがリソースの状態を GET し、それを変更し、PUT で書き戻すが、その間に第三者が状態を変更した「失われた更新」問題を防ぐためのものです。",
usecase: "API が、同時更新の競合を防ぐために更新リクエストに If-Match または If-Unmodified-Since ヘッダーを要求する場合。"
},
{
code: 429, name: "Too Many Requests（リクエストが多すぎます）",
desc: "ユーザーが一定時間内に多すぎるリクエストを送信しました（レート制限）。",
detail: "ユーザーが指定された時間内に多すぎるリクエストを送信したことを示します。レスポンスにはクライアントが新しいリクエストを行う前に待機すべき時間を示す Retry-After ヘッダーが含まれる場合があります。API レート制限の基本です。",
usecase: "API レート制限: クライアントが 1 分あたり 100 リクエストを超えた場合。サーバーは Retry-After: 30 とともに 429 を返します。"
},
{
code: 431, name: "Request Header Fields Too Large（リクエストヘッダーフィールドが大きすぎます）",
desc: "リクエストの HTTP ヘッダーが大きすぎます。",
detail: "サーバーはヘッダーフィールドが大きすぎるためリクエストを処理したくありません。リクエストヘッダーフィールドのサイズを縮小した後に再送信できます。過剰に大きな Cookie によって引き起こされることがよくあります。",
usecase: "時間をかけて蓄積された多すぎる Cookie や大きすぎる Cookie により、リクエストヘッダーがサーバーの制限を超える場合。"
},
{
code: 451, name: "Unavailable For Legal Reasons（法的理由により利用不可）",
desc: "リソースは法的要求により利用できません。",
detail: "ユーザーが法的に提供できないリソースを要求しました。レスポンスには制限を課したエンティティにリンクする rel=blocked-by を含む Link ヘッダーを含める必要があります。華氏 451 度（Fahrenheit 451）にちなんで命名されています。",
usecase: "著作権法、裁判所命令、または政府規制により特定の国でブロックされたコンテンツ。"
},
/* ── 5xx ── */
{
code: 500, name: "Internal Server Error（内部サーバーエラー）",
desc: "サーバーが予期しない条件に遭遇しました。",
detail: "予期しない条件に遭遇し、より具体的なメッセージが適切でない場合に与えられる汎用エラーメッセージです。サーバーが処理方法を知らないエラーに遭遇しました。サーバーサイドエラーのキャッチオールレスポンスです。",
usecase: "サーバーコードの未処理例外、エラーをスローするデータベースクエリ、または設定ミスのあるサーバー。"
},
{
code: 501, name: "Not Implemented（未実装）",
desc: "サーバーはリクエストメソッドをサポートしていません。",
detail: "サーバーはリクエストを実行するために必要な機能をサポートしていません。これはサーバーがリクエストメソッドを認識せず、リソースに対してそれをサポートできない場合の適切なレスポンスです。",
usecase: "GET と POST のみを実装しているサーバーが、サポートしていない PATCH リクエストを受信した場合に 501 を返します。"
},
{
code: 502, name: "Bad Gateway（不正なゲートウェイ）",
desc: "サーバーがアップストリームサーバーから無効なレスポンスを受け取りました。",
detail: "ゲートウェイまたはプロキシとして機能しているサーバーが、リクエストを実行しようとしてアクセスしたアップストリームサーバーから無効なレスポンスを受け取りました。問題はプロキシ自体ではなく、アップストリームサーバーです。",
usecase: "リバースプロキシ（Nginx）がアプリケーションサーバー（Node.js）に到達できない場合、またはアプリケーションサーバーがクラッシュして不正なレスポンスを返す場合。"
},
{
code: 503, name: "Service Unavailable（サービス利用不可）",
desc: "サーバーはリクエストを処理する準備ができていません。",
detail: "サーバーはリクエストを処理する準備ができていません。一般的な原因にはメンテナンスのためにダウンしているサーバーや過負荷のサーバーが含まれます。サービスが一時的に利用できない場合は Retry-After ヘッダーを含めるべきです。",
usecase: "メンテナンス中のサーバー、データベース接続プールの枯渇、またはトラフィックスパイク中にオートスケーリングがまだ機能していない場合。"
},
{
code: 504, name: "Gateway Timeout（ゲートウェイタイムアウト）",
desc: "ゲートウェイがアップストリームサーバーの応答を待機中にタイムアウトしました。",
detail: "ゲートウェイまたはプロキシとして機能しているサーバーが、リクエストを完了するためにアクセスする必要があるアップストリームサーバーからタイムリーなレスポンスを受け取れませんでした。502 とは異なり、アップストリームサーバーは応答しましたが、遅すぎました。",
usecase: "ロードバランサーがアプリケーションサーバーからの応答を待ちすぎる場合（例: 低速なデータベースクエリがタイムアウトを引き起こす）。"
},
{
code: 505, name: "HTTP Version Not Supported（HTTP バージョン非サポート）",
desc: "使用されている HTTP バージョンはサポートされていません。",
detail: "サーバーはリクエストで使用された HTTP バージョンをサポートしていません。レスポンスにはそのバージョンがサポートされていない理由と他にどのプロトコルがサポートされているかの説明を含める必要があります。",
usecase: "HTTP/1.1 までしかサポートしていないサーバーに HTTP/3 リクエストを送信する場合。"
},
{
code: 506, name: "Variant Also Negotiates（バリアントも交渉中）",
desc: "コンテンツネゴシエーションにおける内部サーバー設定エラー。",
detail: "リクエストのトランスペアレントコンテンツネゴシエーションが循環参照を引き起こします。内部サーバー設定エラーを示します。",
usecase: "バリアントリソース自体がコンテンツをネゴシエートするよう設定されているコンテンツネゴシエーションの設定ミス。"
},
{
code: 507, name: "Insufficient Storage（ストレージ不足）",
desc: "サーバーは表現を保存できません（WebDAV）。",
detail: "リクエストを正常に完了するために必要な表現を保存できないため、メソッドをリソースに対して実行できませんでした。一時的な場合があります。",
usecase: "WebDAV: サーバーのストレージクォータが一杯の場合にファイルをアップロードする。"
},
{
code: 508, name: "Loop Detected（ループ検出）",
desc: "サーバーが無限ループを検出しました（WebDAV）。",
detail: "サーバーは Depth: infinity を含むリクエストを処理中に無限ループを検出したため操作を終了しました。WebDAV で使用されます。",
usecase: "WebDAV COPY または MOVE 操作が循環ディレクトリ参照を作成する場合。"
},
{
code: 510, name: "Not Extended（拡張なし）",
desc: "サーバーがリクエストを実行するためにさらなる拡張が必要です。",
detail: "サーバーがそれを実行するためにリクエストへのさらなる拡張が必要です。HTTP 拡張フレームワーク（RFC 2774）で使用されます。",
usecase: "リクエストで指定された HTTP 拡張がサーバーによってサポートされていない場合。"
},
{
code: 511, name: "Network Authentication Required（ネットワーク認証が必要）",
desc: "クライアントはネットワークアクセスを得るために認証が必要です。",
detail: "ネットワークへのアクセスを制御するために使用されるインターセプトプロキシ（例: ホテルや空港のキャプティブポータル）による使用を意図しています。",
usecase: "ホテルの WiFi ポータル: ブラウザーがログインページにリダイレクトされます。インターセプトプロキシが 511 を返します。"
}
];

var CAT_CLASS = {
"1xx": "c1xx", "2xx": "c2xx", "3xx": "c3xx", "4xx": "c4xx", "5xx": "c5xx"
};

function getCat(code) {
return Math.floor(code / 100) + "xx";
}

function buildCard(item) {
var cat = getCat(item.code);
var cls = CAT_CLASS[cat];
var isCommon = COMMON.indexOf(item.code) !== -1;
var id = "hsc-" + item.code;

var commonBadge = isCommon
? '<span class="hsc-common-star">&#9733; よく使われる</span>'
: "";

return [
'<div class="hsc-card ' + cls + (isCommon ? " common" : "") + '" data-code="' + item.code + '" data-cat="' + cat + '" id="' + id + '">',
'<div class="hsc-card-header" onclick="hscToggle(\'' + id + '\')">',
'<span class="hsc-code-num ' + cls + '">' + item.code + '</span>',
'<div class="hsc-card-meta">',
'<div class="hsc-code-name">' + item.name + '</div>',
'<div class="hsc-code-desc">' + item.desc + '</div>',
'</div>',
commonBadge,
'<button class="hsc-copy-btn" onclick="hscCopy(event, ' + item.code + ', \'' + item.name + '\')" aria-label="' + item.code + ' ' + item.name + ' をコピー">コピー</button>',
'<svg class="hsc-chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="6 9 12 15 18 9"/></svg>',
'</div>',
'<div class="hsc-detail">',
'<h4>説明</h4>',
'<p>' + item.detail + '</p>',
'<h4>主な使用例</h4>',
'<div class="hsc-usecase">' + item.usecase + '</div>',
'</div>',
'</div>'
].join("");
}

function buildSection(cat, label, items) {
var cls = CAT_CLASS[cat];
var cards = items.map(buildCard).join("");
return [
'<div class="hsc-section" data-cat="' + cat + '">',
'<div class="hsc-cat-heading">',
'<span class="hsc-cat-badge ' + cls + '">' + cat.toUpperCase() + '</span>',
label,
'</div>',
cards,
'</div>'
].join("");
}

var CATEGORIES = [
{ cat: "1xx", label: "情報" },
{ cat: "2xx", label: "成功" },
{ cat: "3xx", label: "リダイレクト" },
{ cat: "4xx", label: "クライアントエラー" },
{ cat: "5xx", label: "サーバーエラー" }
];

function renderAll() {
var list = document.getElementById("hscList");
var html = "";
CATEGORIES.forEach(function (catDef) {
var items = CODES.filter(function (c) { return getCat(c.code) === catDef.cat; });
html += buildSection(catDef.cat, catDef.label, items);
});
list.innerHTML = html;
}

function filterAndSearch(query, activeCat) {
var q = query.toLowerCase().trim();
var sections = document.querySelectorAll("#hscList .hsc-section");
var visible = 0;

sections.forEach(function (sec) {
var cat = sec.dataset.cat;
var secVisible = 0;
var secCards = sec.querySelectorAll(".hsc-card");
secCards.forEach(function (card) {
var code = card.dataset.code;
var catMatch = activeCat === "all" || cat === activeCat;
var item = CODES.find(function (c) { return String(c.code) === code; });
var textMatch = !q || (
String(item.code).indexOf(q) !== -1 ||
item.name.toLowerCase().indexOf(q) !== -1 ||
item.desc.toLowerCase().indexOf(q) !== -1 ||
item.detail.toLowerCase().indexOf(q) !== -1
);
var show = catMatch && textMatch;
card.style.display = show ? "" : "none";
if (show) { secVisible++; visible++; }
});
sec.style.display = secVisible > 0 ? "" : "none";
});

document.getElementById("hscCount").textContent =
visible + " 件のコードを表示中";
document.getElementById("hscNoResults").style.display =
visible === 0 ? "block" : "none";
}

window.hscToggle = function (id) {
var card = document.getElementById(id);
if (card) card.classList.toggle("open");
};

window.hscCopy = function (e, code, name) {
e.stopPropagation();
var text = code + " " + name;
if (navigator.clipboard) {
navigator.clipboard.writeText(text);
} else {
var ta = document.createElement("textarea");
ta.value = text;
document.body.appendChild(ta);
ta.select();
document.execCommand("copy");
document.body.removeChild(ta);
}
var btn = e.currentTarget;
btn.textContent = "コピー済み!";
btn.classList.add("copied");
setTimeout(function () {
btn.textContent = "コピー";
btn.classList.remove("copied");
}, 1800);
};

document.addEventListener("DOMContentLoaded", function () {
renderAll();
filterAndSearch("", "all");

var activeCat = "all";

document.getElementById("hscSearch").addEventListener("input", function () {
filterAndSearch(this.value, activeCat);
});

document.querySelectorAll(".hsc-filter-btn").forEach(function (btn) {
btn.addEventListener("click", function () {
document.querySelectorAll(".hsc-filter-btn").forEach(function (b) {
b.classList.remove("active");
});
this.classList.add("active");
activeCat = this.dataset.cat;
filterAndSearch(document.getElementById("hscSearch").value, activeCat);
});
});
});
})();
</script>

<!-- freee CTA -->
<div class="hsc-freee-cta">
<h3>freee で業務を自動化しませんか？</h3>
<p>
API 開発をしながら経理・請求書・給与計算もまとめて効率化。<br>
freee は中小企業・フリーランス向けのオールインワン業務管理クラウドです。
</p>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener noreferrer">
freee を無料で試す →
</a>
</div>

</div>

---

### 関連ツール
> 正規表現をテスト → [Regex テスター](/ja/tools/regex-tester/)
> JWT トークンをデコード → [JWT デコーダー](/ja/tools/jwt-decoder/)
> IP アドレス情報を確認 → [IP アドレス情報](/ja/tools/ip-address-info/)

---
title: "プライバシーポリシー ジェネレーター — 無料テンプレートツール"
date: 2025-05-16
description: "Webサイト用プライバシーポリシーを無料生成。個人情報保護法・GDPR対応テンプレート。Cookie・アナリティクス・第三者サービス対応。コピー・ダウンロード即可。"
categories: ["無料ツール"]
slug: "privacy-policy-generator"
ShowToc: false
aliases:
  - "/ja/tools/privacy-policy-generator/"
  - "/ja/tools/privacy-policy-generator/"
cover:
  image: "/images/covers/privacy-policy-generator-ja.png"
  alt: "プライバシーポリシー ジェネレーター"
---

<style>
#pp-app-ja *,
#pp-app-ja *::before,
#pp-app-ja *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#pp-app-ja {
  font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", "Noto Sans JP", "Yu Gothic", -apple-system, BlinkMacSystemFont, sans-serif;
  color: #1e293b;
  max-width: 900px;
  margin: 0 auto;
  padding: 0 0 2rem;
}
#pp-app-ja h2 {
  font-size: 1.05rem;
  font-weight: 700;
  color: #0f172a;
  margin: 1.75rem 0 1rem;
  padding-bottom: 0.4rem;
  border-bottom: 2px solid #e2e8f0;
}
#pp-app-ja .field {
  margin-bottom: 1.1rem;
}
#pp-app-ja label {
  display: block;
  font-size: 0.875rem;
  font-weight: 600;
  color: #374151;
  margin-bottom: 0.35rem;
}
#pp-app-ja input[type="text"],
#pp-app-ja input[type="url"],
#pp-app-ja input[type="email"],
#pp-app-ja input[type="date"] {
  width: 100%;
  padding: 0.55rem 0.75rem;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  font-size: 0.9rem;
  color: #1e293b;
  background: #fff;
  transition: border-color 0.15s;
}
#pp-app-ja input[type="text"]:focus,
#pp-app-ja input[type="url"]:focus,
#pp-app-ja input[type="email"]:focus,
#pp-app-ja input[type="date"]:focus {
  outline: none;
  border-color: #3b82f6;
  box-shadow: 0 0 0 3px rgba(59,130,246,0.12);
}
#pp-app-ja .hint {
  font-size: 0.78rem;
  color: #64748b;
  margin-top: 0.3rem;
}
#pp-app-ja .checkbox-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 0.55rem;
}
#pp-app-ja .checkbox-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.875rem;
  color: #374151;
  cursor: pointer;
  padding: 0.45rem 0.6rem;
  border: 1px solid #e2e8f0;
  border-radius: 6px;
  transition: background 0.12s, border-color 0.12s;
}
#pp-app-ja .checkbox-item:hover {
  background: #f8fafc;
  border-color: #93c5fd;
}
#pp-app-ja .checkbox-item input[type="checkbox"] {
  accent-color: #3b82f6;
  width: 15px;
  height: 15px;
  flex-shrink: 0;
}
#pp-app-ja .toggle-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}
#pp-app-ja .toggle-item {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  font-size: 0.875rem;
  font-weight: 500;
  color: #374151;
  cursor: pointer;
  padding: 0.5rem 0.9rem;
  border: 1px solid #e2e8f0;
  border-radius: 20px;
  transition: all 0.15s;
  user-select: none;
}
#pp-app-ja .toggle-item input[type="checkbox"] {
  accent-color: #3b82f6;
  width: 15px;
  height: 15px;
}
#pp-app-ja .toggle-item.active {
  background: #eff6ff;
  border-color: #3b82f6;
  color: #1d4ed8;
}
#pp-app-ja .btn-generate {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  margin-top: 1.5rem;
  padding: 0.7rem 1.8rem;
  background: #2563eb;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
}
#pp-app-ja .btn-generate:hover {
  background: #1d4ed8;
  transform: translateY(-1px);
}
#pp-app-ja .btn-generate:active {
  transform: translateY(0);
}
#pp-app-ja .output-section {
  display: none;
  margin-top: 2rem;
}
#pp-app-ja .output-section.visible {
  display: block;
}
#pp-app-ja .disclaimer-box {
  background: #fef9c3;
  border: 1px solid #fde047;
  border-radius: 8px;
  padding: 0.85rem 1rem;
  font-size: 0.83rem;
  color: #713f12;
  margin-bottom: 1.25rem;
  line-height: 1.7;
}
#pp-app-ja .disclaimer-box strong {
  display: block;
  margin-bottom: 0.2rem;
  font-size: 0.875rem;
}
#pp-app-ja .action-bar {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  margin-bottom: 1rem;
}
#pp-app-ja .btn-action {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  padding: 0.5rem 1rem;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  font-size: 0.85rem;
  font-weight: 500;
  cursor: pointer;
  background: #fff;
  color: #374151;
  transition: all 0.12s;
}
#pp-app-ja .btn-action:hover {
  background: #f1f5f9;
  border-color: #94a3b8;
}
#pp-app-ja .btn-action.copied {
  background: #dcfce7;
  border-color: #86efac;
  color: #166534;
}
#pp-app-ja .policy-preview {
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  padding: 2rem 2.5rem;
  background: #fff;
  font-size: 0.9rem;
  line-height: 1.85;
  color: #1e293b;
  max-height: 600px;
  overflow-y: auto;
}
#pp-app-ja .policy-preview h1 {
  font-size: 1.4rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: #0f172a;
}
#pp-app-ja .policy-preview h2 {
  font-size: 1rem;
  font-weight: 700;
  margin: 1.5rem 0 0.6rem;
  padding-bottom: 0.3rem;
  border-bottom: 1px solid #e2e8f0;
  color: #0f172a;
}
#pp-app-ja .policy-preview p {
  margin-bottom: 0.8rem;
}
#pp-app-ja .policy-preview ul {
  margin: 0.5rem 0 0.8rem 1.4rem;
}
#pp-app-ja .policy-preview ul li {
  margin-bottom: 0.35rem;
}
#pp-app-ja .policy-preview .last-updated {
  font-size: 0.82rem;
  color: #64748b;
  margin-bottom: 1.2rem;
}
#pp-app-ja .section-cols {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}
@media (max-width: 600px) {
  #pp-app-ja .checkbox-grid {
    grid-template-columns: 1fr 1fr;
  }
  #pp-app-ja .section-cols {
    grid-template-columns: 1fr;
  }
  #pp-app-ja .policy-preview {
    padding: 1rem 1.2rem;
  }
}
@media (max-width: 420px) {
  #pp-app-ja .checkbox-grid {
    grid-template-columns: 1fr;
  }
}
</style>

<div id="pp-app-ja">

<h2>Webサイト情報</h2>

<div class="section-cols">
  <div class="field">
    <label for="ppja-site-name">Webサイト名 <span style="color:#ef4444">*</span></label>
    <input type="text" id="ppja-site-name" placeholder="例：私のブログ">
  </div>
  <div class="field">
    <label for="ppja-site-url">WebサイトURL <span style="color:#ef4444">*</span></label>
    <input type="url" id="ppja-site-url" placeholder="https://example.com">
  </div>
</div>

<div class="section-cols">
  <div class="field">
    <label for="ppja-contact-email">お問い合わせメールアドレス <span style="color:#ef4444">*</span></label>
    <input type="email" id="ppja-contact-email" placeholder="privacy@example.com">
  </div>
  <div class="field">
    <label for="ppja-company-name">会社名・運営者名 <span style="color:#94a3b8">（任意）</span></label>
    <input type="text" id="ppja-company-name" placeholder="例：株式会社〇〇">
  </div>
</div>

<div class="field">
  <label for="ppja-last-updated">最終更新日</label>
  <input type="date" id="ppja-last-updated">
  <div class="hint">本日の日付が自動入力されます。必要に応じて変更してください。</div>
</div>

<h2>収集するデータの種類</h2>
<div class="checkbox-grid">
  <label class="checkbox-item"><input type="checkbox" id="ppja-personal" checked> 個人情報</label>
  <label class="checkbox-item"><input type="checkbox" id="ppja-cookies" checked> Cookie・トラッキング</label>
  <label class="checkbox-item"><input type="checkbox" id="ppja-analytics" checked> アクセス解析</label>
  <label class="checkbox-item"><input type="checkbox" id="ppja-third-party"> 第三者サービス</label>
  <label class="checkbox-item"><input type="checkbox" id="ppja-payment"> 決済情報</label>
  <label class="checkbox-item"><input type="checkbox" id="ppja-location"> 位置情報</label>
</div>

<h2>法令対応オプション</h2>
<div class="toggle-grid" id="ppja-compliance-toggles">
  <label class="toggle-item" id="ppja-lbl-pipa"><input type="checkbox" id="ppja-pipa"> 個人情報保護法（日本）</label>
  <label class="toggle-item" id="ppja-lbl-gdpr"><input type="checkbox" id="ppja-gdpr"> GDPR（EU）</label>
  <label class="toggle-item" id="ppja-lbl-ccpa"><input type="checkbox" id="ppja-ccpa"> CCPA（カリフォルニア州）</label>
  <label class="toggle-item" id="ppja-lbl-coppa"><input type="checkbox" id="ppja-coppa"> COPPA（子どものプライバシー）</label>
</div>

<h2>利用している第三者サービス</h2>
<div class="checkbox-grid">
  <label class="checkbox-item"><input type="checkbox" id="ppja-ga"> Google Analytics</label>
  <label class="checkbox-item"><input type="checkbox" id="ppja-adsense"> Google AdSense</label>
  <label class="checkbox-item"><input type="checkbox" id="ppja-stripe"> Stripe</label>
  <label class="checkbox-item"><input type="checkbox" id="ppja-paypal"> PayPal</label>
  <label class="checkbox-item"><input type="checkbox" id="ppja-mailchimp"> Mailchimp</label>
  <label class="checkbox-item"><input type="checkbox" id="ppja-social"> SNSプラグイン</label>
</div>

<button class="btn-generate" onclick="ppjaGenerate()">プライバシーポリシーを生成する</button>

<div class="output-section" id="ppja-output">
  <div class="disclaimer-box">
    <strong>免責事項</strong>
    このツールで生成されるプライバシーポリシーはテンプレートであり、法律上のアドバイスを構成するものではありません。Webサイトへの掲載前に、必ず弁護士などの法律の専門家にご確認いただくことを強くお勧めします。お客様の具体的な状況や適用される法律によって、必要な内容が異なる場合があります。
  </div>
  <div class="action-bar">
    <button class="btn-action" id="ppja-btn-copy-html" onclick="ppjaCopyHTML()">HTMLとしてコピー</button>
    <button class="btn-action" id="ppja-btn-copy-text" onclick="ppjaCopyText()">テキストとしてコピー</button>
    <button class="btn-action" onclick="ppjaDownload()">.txtでダウンロード</button>
  </div>
  <div class="policy-preview" id="ppja-preview"></div>
</div>

</div>

<script>
(function() {
  // 今日の日付を自動入力
  var today = new Date();
  var yyyy = today.getFullYear();
  var mm = String(today.getMonth() + 1).padStart(2, '0');
  var dd = String(today.getDate()).padStart(2, '0');
  document.getElementById('ppja-last-updated').value = yyyy + '-' + mm + '-' + dd;

  // コンプライアンストグルのアクティブ状態
  var toggleInputs = document.querySelectorAll('#ppja-compliance-toggles input[type="checkbox"]');
  toggleInputs.forEach(function(inp) {
    inp.addEventListener('change', function() {
      var lbl = this.closest('.toggle-item');
      if (this.checked) lbl.classList.add('active');
      else lbl.classList.remove('active');
    });
  });

  window.ppjaGenerate = function() {
    var siteName = document.getElementById('ppja-site-name').value.trim();
    var siteUrl = document.getElementById('ppja-site-url').value.trim();
    var email = document.getElementById('ppja-contact-email').value.trim();
    var company = document.getElementById('ppja-company-name').value.trim();
    var dateVal = document.getElementById('ppja-last-updated').value;

    if (!siteName) { alert('Webサイト名を入力してください。'); return; }
    if (!siteUrl) { alert('WebサイトのURLを入力してください。'); return; }
    if (!email) { alert('お問い合わせ用メールアドレスを入力してください。'); return; }

    var dateStr = dateVal ? new Date(dateVal + 'T00:00:00').toLocaleDateString('ja-JP', {year:'numeric',month:'long',day:'numeric'}) : new Date().toLocaleDateString('ja-JP', {year:'numeric',month:'long',day:'numeric'});
    var owner = company || siteName;

    var hasCookies = document.getElementById('ppja-cookies').checked;
    var hasPersonal = document.getElementById('ppja-personal').checked;
    var hasAnalytics = document.getElementById('ppja-analytics').checked;
    var hasThirdParty = document.getElementById('ppja-third-party').checked;
    var hasPayment = document.getElementById('ppja-payment').checked;
    var hasLocation = document.getElementById('ppja-location').checked;
    var hasPIPA = document.getElementById('ppja-pipa').checked;
    var hasGDPR = document.getElementById('ppja-gdpr').checked;
    var hasCCPA = document.getElementById('ppja-ccpa').checked;
    var hasCOPPA = document.getElementById('ppja-coppa').checked;
    var hasGA = document.getElementById('ppja-ga').checked;
    var hasAdSense = document.getElementById('ppja-adsense').checked;
    var hasStripe = document.getElementById('ppja-stripe').checked;
    var hasPayPal = document.getElementById('ppja-paypal').checked;
    var hasMailchimp = document.getElementById('ppja-mailchimp').checked;
    var hasSocial = document.getElementById('ppja-social').checked;

    var html = '';

    html += '<h1>プライバシーポリシー</h1>';
    html += '<p class="last-updated">最終更新日：' + dateStr + '</p>';

    html += '<h2>第1条（はじめに）</h2>';
    html += '<p><strong>' + esc(siteName) + '</strong>（以下「当サイト」）は、<strong>' + esc(owner) + '</strong>（以下「当社」または「運営者」）が運営しています。当社は、ユーザーの個人情報保護を重要な責務と考え、以下のとおりプライバシーポリシー（以下「本ポリシー」）を定めます。</p>';
    html += '<p>本ポリシーは、当サイト（<a href="' + esc(siteUrl) + '" target="_blank" rel="noopener">' + esc(siteUrl) + '</a>）をご利用いただく際に適用されます。当サイトをご利用になることで、本ポリシーへの同意とみなします。</p>';

    var dataCollected = [];
    if (hasPersonal) dataCollected.push('氏名、メールアドレスなど、ユーザーが自発的に提供する連絡先情報');
    if (hasCookies) dataCollected.push('Cookie識別子およびブラウザセッションデータ');
    if (hasAnalytics) dataCollected.push('閲覧ページ、滞在時間、ブラウザの種類、デバイス情報、参照元など');
    if (hasPayment) dataCollected.push('クレジットカード番号や請求先情報（第三者決済サービスを経由して安全に処理）');
    if (hasLocation) dataCollected.push('IPアドレスに基づくおおよその位置情報');
    if (hasThirdParty) dataCollected.push('第三者サービスとの連携を通じて提供されるデータ');

    if (dataCollected.length > 0) {
      html += '<h2>第2条（収集する情報）</h2>';
      html += '<p>当社は、以下の種類の情報を収集することがあります。</p>';
      html += '<ul>';
      dataCollected.forEach(function(item) { html += '<li>' + item + '</li>'; });
      html += '</ul>';
    }

    html += '<h2>第3条（情報の利用目的）</h2>';
    html += '<p>収集した情報は、以下の目的のために利用します。</p>';
    html += '<ul>';
    html += '<li>当サイトの運営・維持・改善のため</li>';
    if (hasPersonal) html += '<li>お問い合わせへの対応およびカスタマーサポートのため</li>';
    if (hasAnalytics) html += '<li>アクセス状況の分析・把握のため</li>';
    if (hasPayment) html += '<li>決済処理および関連通知の送付のため</li>';
    html += '<li>サービスに関する重要なお知らせの送付のため</li>';
    html += '<li>法令上の義務の履行のため</li>';
    html += '</ul>';

    if (hasCookies) {
      html += '<h2>第4条（Cookieおよびトラッキング技術について）</h2>';
      html += '<p>当サイトでは、Cookie（クッキー）およびこれに類するトラッキング技術を使用することがあります。CookieはWebブラウザに保存される小さなデータファイルです。</p>';
      html += '<p>ブラウザの設定によりCookieを無効化することができますが、その場合、当サイトの一部機能をご利用いただけない場合があります。</p>';
      html += '<p>当サイトが使用するCookieの種類は以下のとおりです。</p>';
      html += '<ul>';
      html += '<li><strong>必須Cookie：</strong>Webサイトの基本的な機能の提供に必要なもの。</li>';
      html += '<li><strong>設定Cookie：</strong>ユーザーの設定や環境設定を記憶するためのもの。</li>';
      if (hasAnalytics) html += '<li><strong>分析Cookie：</strong>訪問者の行動を分析・把握するためのもの。</li>';
      if (hasAdSense) html += '<li><strong>広告Cookie：</strong>ユーザーに関連性の高い広告を配信するためのもの。</li>';
      html += '</ul>';
    }

    var thirdParties = [];
    if (hasGA) thirdParties.push({ name: 'Google Analytics', desc: 'Google LLC が提供するアクセス解析サービスです。Google Analytics はCookieを使用してユーザーの当サイト利用状況を分析します。収集された情報（IPアドレスを含む）はGoogleに送信・保管されます。<a href="https://tools.google.com/dlpage/gaoptout" target="_blank" rel="noopener">Google アナリティクス オプトアウト アドオン</a>をインストールすることで収集を拒否できます。Googleのプライバシーポリシー：<a href="https://policies.google.com/privacy" target="_blank" rel="noopener">https://policies.google.com/privacy</a>' });
    if (hasAdSense) thirdParties.push({ name: 'Google AdSense', desc: 'Google LLC が提供する広告配信サービスです。ユーザーの当サイトや他サイトへの訪問履歴に基づき、Cookieを使用してパーソナライズされた広告を表示することがあります。<a href="https://www.google.com/settings/ads" target="_blank" rel="noopener">Google 広告の設定</a>からオプトアウトできます。' });
    if (hasStripe) thirdParties.push({ name: 'Stripe', desc: 'Stripe, Inc. が提供する決済処理サービスです。Stripeは決済を処理するために必要な支払い情報・取引データを収集することがあります。Stripeのプライバシーポリシー：<a href="https://stripe.com/jp/privacy" target="_blank" rel="noopener">https://stripe.com/jp/privacy</a>' });
    if (hasPayPal) thirdParties.push({ name: 'PayPal', desc: 'PayPal Holdings, Inc. が提供する決済処理サービスです。PayPalのプライバシーポリシー：<a href="https://www.paypal.com/jp/webapps/mpp/ua/privacy-full" target="_blank" rel="noopener">https://www.paypal.com/jp/webapps/mpp/ua/privacy-full</a>' });
    if (hasMailchimp) thirdParties.push({ name: 'Mailchimp', desc: 'The Rocket Science Group LLC が提供するメールマーケティングサービスです。ニュースレターを購読された場合に利用します。Mailchimpのプライバシーポリシー：<a href="https://mailchimp.com/legal/privacy/" target="_blank" rel="noopener">https://mailchimp.com/legal/privacy/</a>' });
    if (hasSocial) thirdParties.push({ name: 'SNSプラグイン', desc: '当サイトには、Facebook・X（旧Twitter）・Instagram・LinkedInなどのSNSのプラグインが含まれている場合があります。これらのプラグインは、お客様のIPアドレスや訪問情報を収集することがあります。各SNSのプライバシーポリシーが適用されます。' });

    if (thirdParties.length > 0) {
      html += '<h2>第5条（第三者サービスについて）</h2>';
      html += '<p>当サイトでは、以下の第三者サービスを利用しています。各サービスには独自のプライバシーポリシーがあります。</p>';
      thirdParties.forEach(function(tp) {
        html += '<p><strong>' + tp.name + '：</strong>' + tp.desc + '</p>';
      });
    }

    var sectionNum = thirdParties.length > 0 ? 6 : 5;

    html += '<h2>第' + toJaNum(sectionNum) + '条（データの保存期間）</h2>';
    html += '<p>当社は、本ポリシーに記載された目的の達成に必要な期間、または法令で定める期間を超えて個人情報を保持しません。不要となった情報は、安全な方法で削除または匿名化します。</p>';
    sectionNum++;

    html += '<h2>第' + toJaNum(sectionNum) + '条（安全管理措置）</h2>';
    html += '<p>当社は、お客様の個人情報を不正アクセス・改ざん・漏洩・紛失・破壊から守るため、適切な技術的・組織的安全管理措置を講じています。ただし、インターネット上のデータ送信や電子的なデータ保存について、完全な安全性を保証するものではありません。</p>';
    sectionNum++;

    if (hasPIPA) {
      html += '<h2>第' + toJaNum(sectionNum) + '条（個人情報保護法に基づく開示・訂正等）</h2>';
      html += '<p>当社は、日本の個人情報の保護に関する法律（個人情報保護法）を遵守します。ユーザーは、自己の個人情報について、以下の請求を行うことができます。</p>';
      html += '<ul>';
      html += '<li><strong>開示請求：</strong>当社が保有する自己の個人情報の開示を請求することができます。</li>';
      html += '<li><strong>訂正・追加・削除請求：</strong>個人情報の内容が事実でない場合、訂正・追加または削除を請求することができます。</li>';
      html += '<li><strong>利用停止・消去請求：</strong>法令に定める場合、個人情報の利用停止または消去を請求することができます。</li>';
      html += '<li><strong>苦情の申し出：</strong>個人情報の取り扱いに関する苦情を申し出ることができます。</li>';
      html += '</ul>';
      html += '<p>これらの請求については、<a href="mailto:' + esc(email) + '">' + esc(email) + '</a> までご連絡ください。合理的な期間内に対応いたします。</p>';
      sectionNum++;
    }

    if (hasCOPPA) {
      html += '<h2>第' + toJaNum(sectionNum) + '条（お子様のプライバシーについて）</h2>';
      html += '<p>当サイトは13歳未満のお子様を対象としていません。当社は、13歳未満の方から意図的に個人情報を収集しません。13歳未満のお子様が個人情報を提供したことが判明した場合は、速やかに削除いたします。保護者の方で、お子様が個人情報を提供した可能性がある場合は、直ちに <a href="mailto:' + esc(email) + '">' + esc(email) + '</a> までご連絡ください。</p>';
      sectionNum++;
    }

    if (hasGDPR) {
      html += '<h2>第' + toJaNum(sectionNum) + '条（GDPRに基づくお客様の権利）</h2>';
      html += '<p>欧州経済領域（EEA）にお住まいのお客様は、以下のデータ保護に関する権利を有します。</p>';
      html += '<ul>';
      html += '<li><strong>アクセス権：</strong>当社が保有するご自身の個人データのコピーを請求できます。</li>';
      html += '<li><strong>訂正権：</strong>不正確または不完全なデータの訂正を請求できます。</li>';
      html += '<li><strong>削除権（忘れられる権利）：</strong>一定の条件のもと、個人データの削除を請求できます。</li>';
      html += '<li><strong>処理の制限権：</strong>個人データの処理の制限を請求できます。</li>';
      html += '<li><strong>データポータビリティ権：</strong>構造化された機械可読形式でデータを受け取ることができます。</li>';
      html += '<li><strong>異議申し立て権：</strong>正当な利益に基づく処理に対して異議を申し立てることができます。</li>';
      html += '<li><strong>同意の撤回：</strong>同意に基づく処理について、いつでも同意を撤回することができます。</li>';
      html += '</ul>';
      html += '<p>これらの権利を行使する場合は、<a href="mailto:' + esc(email) + '">' + esc(email) + '</a> までご連絡ください。30日以内に対応いたします。</p>';
      sectionNum++;
    }

    if (hasCCPA) {
      html += '<h2>第' + toJaNum(sectionNum) + '条（CCPAに基づくカリフォルニア州居住者の権利）</h2>';
      html += '<p>カリフォルニア州にお住まいの方は、カリフォルニア州消費者プライバシー法（CCPA）に基づき、以下の権利を有します。</p>';
      html += '<ul>';
      html += '<li><strong>知る権利：</strong>当社が収集した個人情報の種類および具体的な内容の開示を求める権利。</li>';
      html += '<li><strong>削除の権利：</strong>一定の例外を除き、当社が収集した個人情報の削除を求める権利。</li>';
      html += '<li><strong>販売のオプトアウト：</strong>当社はお客様の個人情報を販売しません。</li>';
      html += '<li><strong>差別禁止：</strong>権利を行使したことを理由に差別的な扱いを受けません。</li>';
      html += '</ul>';
      html += '<p>CCPA上の権利行使については、<a href="mailto:' + esc(email) + '">' + esc(email) + '</a> までご連絡ください。</p>';
      sectionNum++;
    }

    html += '<h2>第' + toJaNum(sectionNum) + '条（外部リンクについて）</h2>';
    html += '<p>当サイトには、第三者が運営するWebサイトへのリンクが含まれる場合があります。リンク先のサイトは本ポリシーの適用外であり、当社は各リンク先のプライバシー慣行について責任を負いません。リンク先サイトのプライバシーポリシーを必ずご確認ください。</p>';
    sectionNum++;

    html += '<h2>第' + toJaNum(sectionNum) + '条（プライバシーポリシーの変更）</h2>';
    html += '<p>当社は、必要に応じて本ポリシーを変更することがあります。変更後のポリシーは本ページに掲載した時点から効力を生じ、「最終更新日」が更新されます。定期的にご確認いただくことをお勧めします。</p>';
    sectionNum++;

    html += '<h2>第' + toJaNum(sectionNum) + '条（お問い合わせ）</h2>';
    html += '<p>本ポリシーに関するご質問・ご意見・各種ご請求については、下記までご連絡ください。</p>';
    html += '<ul>';
    html += '<li><strong>メールアドレス：</strong><a href="mailto:' + esc(email) + '">' + esc(email) + '</a></li>';
    if (siteUrl) html += '<li><strong>Webサイト：</strong><a href="' + esc(siteUrl) + '" target="_blank" rel="noopener">' + esc(siteUrl) + '</a></li>';
    if (company) html += '<li><strong>運営者：</strong>' + esc(company) + '</li>';
    html += '</ul>';
    html += '<p>以上</p>';

    document.getElementById('ppja-preview').innerHTML = html;
    var out = document.getElementById('ppja-output');
    out.classList.add('visible');
    out.scrollIntoView({ behavior: 'smooth', block: 'start' });
  };

  function toJaNum(n) {
    var kanji = ['一','二','三','四','五','六','七','八','九','十','十一','十二','十三','十四','十五','十六','十七','十八','十九','二十'];
    return n >= 1 && n <= 20 ? kanji[n-1] : String(n);
  }

  function esc(str) {
    return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  window.ppjaCopyHTML = function() {
    var html = document.getElementById('ppja-preview').innerHTML;
    navigator.clipboard.writeText(html).then(function() {
      flashBtn('ppja-btn-copy-html', 'コピーしました！');
    }).catch(function() {
      fallbackCopy(html);
    });
  };

  window.ppjaCopyText = function() {
    var text = document.getElementById('ppja-preview').innerText;
    navigator.clipboard.writeText(text).then(function() {
      flashBtn('ppja-btn-copy-text', 'コピーしました！');
    }).catch(function() {
      fallbackCopy(text);
    });
  };

  window.ppjaDownload = function() {
    var text = document.getElementById('ppja-preview').innerText;
    var siteName = document.getElementById('ppja-site-name').value.trim() || 'website';
    var filename = siteName.replace(/\s+/g, '-') + '-privacy-policy.txt';
    var blob = new Blob([text], { type: 'text/plain;charset=utf-8' });
    var a = document.createElement('a');
    a.href = URL.createObjectURL(blob);
    a.download = filename;
    a.click();
    URL.revokeObjectURL(a.href);
  };

  function flashBtn(id, label) {
    var btn = document.getElementById(id);
    var orig = btn.textContent;
    btn.textContent = label;
    btn.classList.add('copied');
    setTimeout(function() { btn.textContent = orig; btn.classList.remove('copied'); }, 2000);
  }

  function fallbackCopy(text) {
    var ta = document.createElement('textarea');
    ta.value = text;
    ta.style.position = 'fixed';
    ta.style.opacity = '0';
    document.body.appendChild(ta);
    ta.select();
    document.execCommand('copy');
    document.body.removeChild(ta);
  }
})();
</script>

---

### 関連ツール

> メタタグを作成 → [メタタグジェネレーター](/ja/tools/meta-tag-generator/)

> robots.txtを生成 → [Robots.txtジェネレーター](/ja/tools/robots-txt-generator/)

> マークダウン表を作成 → [マークダウン表作成ツール](/ja/tools/markdown-table-generator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

---
title: "DNSレコードガイド — 設定ヘルパー"
date: 2025-05-16
description: "DNSレコードタイプ完全リファレンス＆設定例。GitHub Pages・Vercel・Google Workspace等のDNS設定を生成。レコードを即コピー。"
categories: ["無料ツール"]
slug: "dns-record-guide"
ShowToc: false
cover:
  image: "/images/covers/dns-record-guide-ja.png"
  alt: "DNSレコードガイド"
---

<div id="dns-app">

<style>
#dns-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Yu Gothic UI", "Segoe UI", sans-serif;
  max-width: 900px;
  margin: 0 auto;
  color: #1a1a2e;
  line-height: 1.7;
}
#dns-app *, #dns-app *::before, #dns-app *::after {
  box-sizing: border-box;
}
#dns-app h2 {
  font-size: 1.35rem;
  font-weight: 700;
  margin: 2rem 0 1rem;
  color: #1a1a2e;
  border-bottom: 2px solid #e0e7ff;
  padding-bottom: 0.4rem;
}
#dns-app h3 {
  font-size: 1.02rem;
  font-weight: 600;
  margin: 0 0 0.4rem;
  color: #1a1a2e;
}

/* ---------- 設定ジェネレーター ---------- */
#dns-config-generator {
  background: linear-gradient(135deg, #f0f4ff 0%, #e8f5e9 100%);
  border: 1px solid #c7d7fc;
  border-radius: 12px;
  padding: 1.5rem;
  margin-bottom: 2rem;
}
#dns-config-generator label {
  display: block;
  font-weight: 600;
  font-size: 0.9rem;
  color: #374151;
  margin-bottom: 0.3rem;
}
#dns-domain-input {
  width: 100%;
  padding: 0.6rem 0.9rem;
  border: 1px solid #a5b4fc;
  border-radius: 8px;
  font-size: 1rem;
  margin-bottom: 1rem;
  outline: none;
  transition: border 0.2s;
  background: #fff;
}
#dns-domain-input:focus {
  border-color: #6366f1;
  box-shadow: 0 0 0 3px rgba(99,102,241,0.15);
}
#dns-preset-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(145px, 1fr));
  gap: 0.5rem;
  margin-bottom: 1rem;
}
.dns-preset-btn {
  padding: 0.55rem 0.7rem;
  border: 2px solid #c7d7fc;
  border-radius: 8px;
  background: #fff;
  cursor: pointer;
  font-size: 0.82rem;
  font-weight: 600;
  color: #374151;
  transition: all 0.15s;
  text-align: center;
}
.dns-preset-btn:hover,
.dns-preset-btn.dns-preset-active {
  background: #6366f1;
  border-color: #6366f1;
  color: #fff;
}
#dns-generate-btn {
  display: inline-block;
  padding: 0.65rem 1.6rem;
  background: #6366f1;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 0.95rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.2s;
}
#dns-generate-btn:hover { background: #4f46e5; }

/* ---------- 結果エリア ---------- */
#dns-results {
  margin-top: 1.5rem;
  display: none;
}
#dns-results.dns-visible { display: block; }
.dns-result-header {
  font-weight: 700;
  font-size: 1rem;
  color: #4f46e5;
  margin-bottom: 0.8rem;
}
.dns-record-card {
  background: #fff;
  border: 1px solid #e0e7ff;
  border-radius: 10px;
  padding: 1rem 1.1rem;
  margin-bottom: 0.75rem;
  position: relative;
}
.dns-record-type-badge {
  display: inline-block;
  padding: 0.2rem 0.55rem;
  border-radius: 5px;
  font-size: 0.72rem;
  font-weight: 800;
  letter-spacing: 0.04em;
  margin-right: 0.5rem;
  vertical-align: middle;
}
.dns-badge-A    { background: #dbeafe; color: #1d4ed8; }
.dns-badge-AAAA { background: #ede9fe; color: #6d28d9; }
.dns-badge-CNAME{ background: #dcfce7; color: #166534; }
.dns-badge-MX   { background: #fef9c3; color: #854d0e; }
.dns-badge-TXT  { background: #fce7f3; color: #9d174d; }
.dns-badge-NS   { background: #e0f2fe; color: #0369a1; }
.dns-badge-SRV  { background: #ffedd5; color: #9a3412; }
.dns-badge-CAA  { background: #f3e8ff; color: #7e22ce; }
.dns-badge-PTR  { background: #d1fae5; color: #065f46; }
.dns-badge-SOA  { background: #fee2e2; color: #991b1b; }
.dns-record-row {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr auto;
  gap: 0.5rem;
  align-items: center;
  margin-top: 0.5rem;
  font-size: 0.85rem;
}
.dns-record-label {
  font-size: 0.72rem;
  font-weight: 700;
  color: #6b7280;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 0.1rem;
}
.dns-record-value {
  font-family: "SF Mono", "Fira Code", "Fira Mono", monospace;
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 5px;
  padding: 0.25rem 0.5rem;
  word-break: break-all;
  font-size: 0.82rem;
  color: #1e293b;
}
.dns-copy-btn {
  padding: 0.3rem 0.7rem;
  background: #6366f1;
  color: #fff;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 0.78rem;
  font-weight: 600;
  white-space: nowrap;
  transition: background 0.15s;
  align-self: end;
}
.dns-copy-btn:hover  { background: #4f46e5; }
.dns-copy-btn.copied { background: #16a34a; }
.dns-record-note {
  font-size: 0.78rem;
  color: #6b7280;
  margin-top: 0.5rem;
  font-style: italic;
}

/* ---------- リファレンス ---------- */
#dns-reference-section { margin-top: 2.5rem; }
.dns-type-card {
  background: #fff;
  border: 1px solid #e0e7ff;
  border-radius: 10px;
  padding: 1.1rem 1.2rem;
  margin-bottom: 1rem;
}
.dns-type-card-header {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 0.6rem;
}
.dns-type-desc {
  font-size: 0.88rem;
  color: #374151;
  margin-bottom: 0.5rem;
}
.dns-type-example {
  font-family: "SF Mono", "Fira Code", monospace;
  font-size: 0.8rem;
  background: #f1f5f9;
  border-left: 3px solid #6366f1;
  padding: 0.5rem 0.8rem;
  border-radius: 0 6px 6px 0;
  color: #1e293b;
  white-space: pre;
  overflow-x: auto;
}
.dns-type-use {
  font-size: 0.78rem;
  color: #6b7280;
  margin-top: 0.4rem;
}

/* ---------- クロスリンク ---------- */
#dns-crosslinks {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  margin-top: 1.5rem;
}
.dns-crosslink {
  display: inline-block;
  padding: 0.45rem 1rem;
  background: #e0e7ff;
  color: #4338ca;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 600;
  text-decoration: none;
  transition: background 0.15s;
}
.dns-crosslink:hover {
  background: #c7d7fc;
  text-decoration: none;
}

/* ---------- freee CTA ---------- */
#dns-freee-cta {
  margin-top: 2.5rem;
  background: linear-gradient(135deg, #fff7ed 0%, #fef3c7 100%);
  border: 1px solid #fed7aa;
  border-radius: 12px;
  padding: 1.4rem 1.6rem;
}
#dns-freee-cta h3 {
  font-size: 1rem;
  font-weight: 700;
  color: #92400e;
  margin-bottom: 0.5rem;
}
#dns-freee-cta p {
  font-size: 0.88rem;
  color: #78350f;
  margin-bottom: 0.8rem;
}
.dns-freee-btn {
  display: inline-block;
  padding: 0.6rem 1.4rem;
  background: #f97316;
  color: #fff;
  border-radius: 8px;
  font-size: 0.9rem;
  font-weight: 700;
  text-decoration: none;
  transition: background 0.15s;
}
.dns-freee-btn:hover {
  background: #ea580c;
  text-decoration: none;
  color: #fff;
}

/* ---------- レスポンシブ ---------- */
@media (max-width: 600px) {
  #dns-preset-grid {
    grid-template-columns: repeat(2, 1fr);
  }
  .dns-record-row {
    grid-template-columns: 1fr 1fr;
  }
  .dns-copy-btn {
    grid-column: 1 / -1;
    width: 100%;
    margin-top: 0.3rem;
  }
}
</style>

## DNS設定ヘルパー

ドメイン名を入力し、利用するサービスを選択すると、そのままコピーできるDNSレコードが生成されます。

<div id="dns-config-generator">
  <label for="dns-domain-input">ドメイン名</label>
  <input type="text" id="dns-domain-input" placeholder="example.com" autocomplete="off" spellcheck="false" />

  <label style="margin-bottom:0.5rem;">プリセット設定を選択</label>
  <div id="dns-preset-grid">
    <button class="dns-preset-btn dns-preset-active" data-preset="github-pages">GitHub Pages</button>
    <button class="dns-preset-btn" data-preset="vercel">Vercel</button>
    <button class="dns-preset-btn" data-preset="netlify">Netlify</button>
    <button class="dns-preset-btn" data-preset="cloudflare">Cloudflare</button>
    <button class="dns-preset-btn" data-preset="google-workspace">Google Workspace</button>
    <button class="dns-preset-btn" data-preset="microsoft-365">Microsoft 365</button>
    <button class="dns-preset-btn" data-preset="cdn-basic">CDN（汎用）</button>
    <button class="dns-preset-btn" data-preset="email-basic">メールのみ</button>
  </div>

  <button id="dns-generate-btn">DNSレコードを生成する</button>

  <div id="dns-results">
    <div class="dns-result-header" id="dns-result-title"></div>
    <div id="dns-record-list"></div>
  </div>
</div>

<script>
(function() {
  const PRESETS = {
    "github-pages": {
      label: "GitHub Pages",
      records: [
        { type:"A",     host:"@",    value:"185.199.108.153", ttl:"3600", note:"GitHub Pages IP #1" },
        { type:"A",     host:"@",    value:"185.199.109.153", ttl:"3600", note:"GitHub Pages IP #2" },
        { type:"A",     host:"@",    value:"185.199.110.153", ttl:"3600", note:"GitHub Pages IP #3" },
        { type:"A",     host:"@",    value:"185.199.111.153", ttl:"3600", note:"GitHub Pages IP #4" },
        { type:"AAAA",  host:"@",    value:"2606:50c0:8000::153", ttl:"3600", note:"GitHub Pages IPv6 #1" },
        { type:"AAAA",  host:"@",    value:"2606:50c0:8001::153", ttl:"3600", note:"GitHub Pages IPv6 #2" },
        { type:"CNAME", host:"www",  value:"yourusername.github.io", ttl:"3600", note:"「yourusername」をGitHubユーザー名に置き換えてください" },
        { type:"TXT",   host:"@",    value:"v=spf1 -all", ttl:"3600", note:"基本SPF設定。このドメインからメールを送信する場合は変更が必要です" },
      ]
    },
    "vercel": {
      label: "Vercel",
      records: [
        { type:"A",     host:"@",    value:"76.76.21.21",      ttl:"3600", note:"Vercel グローバルIP" },
        { type:"CNAME", host:"www",  value:"cname.vercel-dns.com", ttl:"3600", note:"Vercel www用CNAME" },
        { type:"TXT",   host:"@",    value:"v=spf1 -all",      ttl:"3600", note:"基本SPF設定" },
      ]
    },
    "netlify": {
      label: "Netlify",
      records: [
        { type:"A",     host:"@",    value:"75.2.60.5",        ttl:"3600", note:"Netlifyロードバランサーの固定IP" },
        { type:"CNAME", host:"www",  value:"apex-loadbalancer.netlify.com", ttl:"3600", note:"Netlify www用CNAME" },
        { type:"TXT",   host:"@",    value:"v=spf1 -all",      ttl:"3600", note:"基本SPF設定" },
      ]
    },
    "cloudflare": {
      label: "Cloudflare（プロキシ）",
      records: [
        { type:"A",     host:"@",    value:"192.0.2.1",        ttl:"auto", note:"オリジンサーバーのIPに置き換えてください。Cloudflareプロキシ（橙色の雲）を有効にしてください" },
        { type:"CNAME", host:"www",  value:"example.com",      ttl:"auto", note:"example.comをご自身のドメインに置き換え、プロキシを有効化" },
        { type:"TXT",   host:"@",    value:"v=spf1 include:_spf.mx.cloudflare.net ~all", ttl:"3600", note:"Cloudflareメールルーティング利用時のSPF設定" },
        { type:"MX",    host:"@",    value:"route1.mx.cloudflare.net", ttl:"3600", note:"Cloudflareメールルーティング MX #1（優先度13）" },
        { type:"MX",    host:"@",    value:"route2.mx.cloudflare.net", ttl:"3600", note:"MX #2（優先度30）" },
        { type:"MX",    host:"@",    value:"route3.mx.cloudflare.net", ttl:"3600", note:"MX #3（優先度2）" },
      ]
    },
    "google-workspace": {
      label: "Google Workspace",
      records: [
        { type:"MX",  host:"@", value:"aspmx.l.google.com",        ttl:"3600", note:"Google MX — 優先度1（最高）" },
        { type:"MX",  host:"@", value:"alt1.aspmx.l.google.com",   ttl:"3600", note:"優先度5" },
        { type:"MX",  host:"@", value:"alt2.aspmx.l.google.com",   ttl:"3600", note:"優先度5" },
        { type:"MX",  host:"@", value:"alt3.aspmx.l.google.com",   ttl:"3600", note:"優先度10" },
        { type:"MX",  host:"@", value:"alt4.aspmx.l.google.com",   ttl:"3600", note:"優先度10" },
        { type:"TXT", host:"@", value:"v=spf1 include:_spf.google.com ~all", ttl:"3600", note:"Google Workspace SPF設定" },
        { type:"TXT", host:"@", value:"google-site-verification=ここにコードを入力", ttl:"3600", note:"ドメイン確認コード — Google管理コンソールで取得" },
        { type:"CNAME", host:"mail", value:"ghs.google.com",        ttl:"3600", note:"カスタムメールURL（mail.yourdomain.com）" },
        { type:"CNAME", host:"calendar", value:"ghs.google.com",    ttl:"3600", note:"カスタムカレンダーURL" },
        { type:"CNAME", host:"drive",    value:"ghs.google.com",    ttl:"3600", note:"カスタムドライブURL" },
        { type:"TXT", host:"_dmarc", value:"v=DMARC1; p=quarantine; rua=mailto:dmarc@DOMAIN; pct=100", ttl:"3600", note:"DMARCポリシー — DOMAINをご自身のドメインに置き換えてください" },
      ]
    },
    "microsoft-365": {
      label: "Microsoft 365",
      records: [
        { type:"MX",   host:"@",           value:"DOMAIN-com.mail.protection.outlook.com", ttl:"3600", note:"「DOMAIN-com」をドメイン名（ハイフン区切り）に置き換え。M365管理センターで確認" },
        { type:"TXT",  host:"@",           value:"v=spf1 include:spf.protection.outlook.com -all", ttl:"3600", note:"Microsoft 365 SPF設定" },
        { type:"TXT",  host:"@",           value:"MS=msXXXXXXXX",  ttl:"3600", note:"ドメイン確認コード — M365管理センターで取得" },
        { type:"CNAME", host:"autodiscover", value:"autodiscover.outlook.com", ttl:"3600", note:"Outlook自動検出設定" },
        { type:"CNAME", host:"selector1._domainkey", value:"selector1-DOMAIN-com._domainkey.TENANT.onmicrosoft.com", ttl:"3600", note:"DKIM セレクター1 — M365管理センターで正確な値を確認" },
        { type:"CNAME", host:"selector2._domainkey", value:"selector2-DOMAIN-com._domainkey.TENANT.onmicrosoft.com", ttl:"3600", note:"DKIM セレクター2" },
        { type:"TXT",  host:"_dmarc",      value:"v=DMARC1; p=reject; rua=mailto:dmarc@DOMAIN; pct=100", ttl:"3600", note:"DMARCポリシー — DOMAINをご自身のドメインに置き換え" },
        { type:"SRV",  host:"_sip._tls",   value:"100 1 443 sipdir.online.lync.com", ttl:"3600", note:"Teams / Skype for Business" },
        { type:"SRV",  host:"_sipfederationtls._tcp", value:"100 1 5061 sipfed.online.lync.com", ttl:"3600", note:"Teamsフェデレーション設定" },
      ]
    },
    "cdn-basic": {
      label: "CDN（汎用）",
      records: [
        { type:"A",     host:"@",    value:"オリジンサーバーのIP",  ttl:"3600", note:"ご自身のオリジンサーバーのIPアドレスに置き換えてください" },
        { type:"CNAME", host:"www",  value:"cdn.example.com", ttl:"3600", note:"CDNプロバイダーから提供されるCNAMEに置き換えてください" },
        { type:"CNAME", host:"static", value:"cdn.example.com", ttl:"3600", note:"静的アセット用サブドメイン（任意）" },
        { type:"TXT",   host:"@",    value:"v=spf1 include:メールプロバイダー ~all", ttl:"3600", note:"ご利用のメールプロバイダーに合わせて変更してください" },
        { type:"CAA",   host:"@",    value:"0 issue \"letsencrypt.org\"", ttl:"3600", note:"Let's Encryptによる証明書発行を許可" },
        { type:"CAA",   host:"@",    value:"0 issuewild \"letsencrypt.org\"", ttl:"3600", note:"ワイルドカード証明書の発行を許可" },
      ]
    },
    "email-basic": {
      label: "メールのみ（汎用）",
      records: [
        { type:"MX",  host:"@",      value:"mail.DOMAIN",     ttl:"3600", note:"メインのメールサーバー — 優先度10を設定" },
        { type:"A",   host:"mail",   value:"メールサーバーのIP", ttl:"3600", note:"メールサーバーのAレコード" },
        { type:"TXT", host:"@",      value:"v=spf1 mx ~all",  ttl:"3600", note:"SPF: MXサーバーからの送信を許可" },
        { type:"TXT", host:"_dmarc", value:"v=DMARC1; p=none; rua=mailto:dmarc@DOMAIN; pct=100", ttl:"3600", note:"DMARCモニタリングモード — 分析後にp=quarantineまたはp=rejectへ変更を推奨" },
        { type:"PTR", host:"メールサーバーのIP", value:"mail.DOMAIN", ttl:"3600", note:"逆引きDNS — ホスティングプロバイダーに設定を依頼してください" },
      ]
    }
  };

  let selectedPreset = "github-pages";

  const domainInput  = document.getElementById("dns-domain-input");
  const presetBtns   = document.querySelectorAll(".dns-preset-btn");
  const generateBtn  = document.getElementById("dns-generate-btn");
  const results      = document.getElementById("dns-results");
  const resultTitle  = document.getElementById("dns-result-title");
  const recordList   = document.getElementById("dns-record-list");

  presetBtns.forEach(btn => {
    btn.addEventListener("click", () => {
      presetBtns.forEach(b => b.classList.remove("dns-preset-active"));
      btn.classList.add("dns-preset-active");
      selectedPreset = btn.dataset.preset;
    });
  });

  function sanitizeDomain(raw) {
    return raw.trim().toLowerCase().replace(/^https?:\/\//,"").replace(/\/.*$/,"").replace(/^www\./,"") || "example.com";
  }

  function buildRecordHTML(rec, domain) {
    const host  = rec.host.replace(/DOMAIN/g, domain);
    const value = rec.value.replace(/DOMAIN/g, domain).replace(/example\.com/g, domain);
    const copyText = `${host}\t${rec.type}\t${rec.ttl}\t${value}`;
    return `
      <div class="dns-record-card">
        <span class="dns-record-type-badge dns-badge-${rec.type}">${rec.type}</span>
        <strong style="font-size:0.88rem;color:#4f46e5;">${host === "@" ? domain : host + "." + domain}</strong>
        <div class="dns-record-row">
          <div>
            <div class="dns-record-label">ホスト名</div>
            <div class="dns-record-value">${escHtml(host)}</div>
          </div>
          <div>
            <div class="dns-record-label">値 / 参照先</div>
            <div class="dns-record-value">${escHtml(value)}</div>
          </div>
          <div>
            <div class="dns-record-label">TTL</div>
            <div class="dns-record-value">${escHtml(rec.ttl)}</div>
          </div>
          <button class="dns-copy-btn" data-copy="${escAttr(copyText)}">コピー</button>
        </div>
        ${rec.note ? `<div class="dns-record-note">${escHtml(rec.note)}</div>` : ""}
      </div>`;
  }

  function escHtml(s) {
    return s.replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;").replace(/"/g,"&quot;");
  }
  function escAttr(s) {
    return s.replace(/"/g,"&quot;");
  }

  generateBtn.addEventListener("click", () => {
    const domain  = sanitizeDomain(domainInput.value);
    const preset  = PRESETS[selectedPreset];
    resultTitle.textContent = `${domain} — ${preset.label} のDNSレコード`;
    recordList.innerHTML = preset.records.map(r => buildRecordHTML(r, domain)).join("");
    results.classList.add("dns-visible");

    recordList.querySelectorAll(".dns-copy-btn").forEach(btn => {
      btn.addEventListener("click", () => {
        navigator.clipboard.writeText(btn.dataset.copy).then(() => {
          btn.textContent = "コピー済!";
          btn.classList.add("copied");
          setTimeout(() => { btn.textContent = "コピー"; btn.classList.remove("copied"); }, 2000);
        });
      });
    });
  });

  domainInput.addEventListener("keydown", e => { if (e.key === "Enter") generateBtn.click(); });
})();
</script>

---

## DNSレコードタイプ リファレンス

<div id="dns-reference-section">

<div class="dns-type-card">
<div class="dns-type-card-header">
  <span class="dns-record-type-badge dns-badge-A">A</span>
  <h3>Aレコード — IPv4アドレス</h3>
</div>
<div class="dns-type-desc">ホスト名をIPv4アドレスにマッピングする、最も基本的なDNSレコードです。ブラウザがドメインにアクセスする際、DNSはAレコードを参照してどのサーバーに接続するかを決定します。</div>
<div class="dns-type-example">example.com.     3600  IN  A  93.184.216.34
www.example.com. 3600  IN  A  93.184.216.34</div>
<div class="dns-type-use"><strong>使用場面：</strong>ドメインをWebサーバー・メールサーバー・その他IPv4アドレスに向ける場合。</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
  <span class="dns-record-type-badge dns-badge-AAAA">AAAA</span>
  <h3>AAAAレコード — IPv6アドレス</h3>
</div>
<div class="dns-type-desc">ホスト名をIPv6アドレスにマッピングします。Aレコードと同じ役割ですが、IPv6に対応した現代的なインフラ向けです。GitHub Pages・Cloudflare等の主要CDNではAレコードと合わせてAAAAレコードも設定することを推奨します。</div>
<div class="dns-type-example">example.com.  3600  IN  AAAA  2606:2800:220:1:248:1893:25c8:1946</div>
<div class="dns-type-use"><strong>使用場面：</strong>サーバーがIPv6をサポートしている場合（GitHub Pages、Cloudflare、主要CDN等）。</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
  <span class="dns-record-type-badge dns-badge-CNAME">CNAME</span>
  <h3>CNAMEレコード — 正規名（エイリアス）</h3>
</div>
<div class="dns-type-desc">あるホスト名を別のホスト名のエイリアスとして定義します。IPアドレスではなく別のドメイン名を指します。標準DNSではゾーン頂点（@）では使用不可です（ALIAS/ANAMEレコードを使用してください）。最終的にAまたはAAAAレコードに解決される必要があります。</div>
<div class="dns-type-example">www.example.com.   3600  IN  CNAME  example.com.
blog.example.com.  3600  IN  CNAME  my-site.netlify.app.</div>
<div class="dns-type-use"><strong>使用場面：</strong>サブドメインをVercel・Netlify・GitHub Pages（www）・CDNホスト名等に向ける場合。</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
  <span class="dns-record-type-badge dns-badge-MX">MX</span>
  <h3>MXレコード — メールエクスチェンジャー</h3>
</div>
<div class="dns-type-desc">ドメイン宛てのメールを受信するメールサーバーを指定します。複数設定でき、優先度（数値が小さいほど高優先）を割り当てます。値にはIPアドレスではなくホスト名を指定します。</div>
<div class="dns-type-example">example.com.  3600  IN  MX  1   aspmx.l.google.com.
example.com.  3600  IN  MX  5   alt1.aspmx.l.google.com.
example.com.  3600  IN  MX  10  alt2.aspmx.l.google.com.</div>
<div class="dns-type-use"><strong>使用場面：</strong>Google Workspace・Microsoft 365・Fastmail・ProtonMail等のメール設定時。</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
  <span class="dns-record-type-badge dns-badge-TXT">TXT</span>
  <h3>TXTレコード — テキスト情報</h3>
</div>
<div class="dns-type-desc">任意のテキストデータを格納します。ドメイン所有権確認、メール認証（SPF・DKIM・DMARC）、各種サービス設定に広く利用されています。同一ドメインに複数のTXTレコードを設定できます。</div>
<div class="dns-type-example"># SPF — 送信許可サーバーを宣言
example.com.   3600  IN  TXT  "v=spf1 include:_spf.google.com ~all"

# DMARC — メールポリシー設定
_dmarc.example.com.  3600  IN  TXT  "v=DMARC1; p=reject; rua=mailto:dmarc@example.com"

# DKIM — 署名公開鍵
selector._domainkey.example.com.  3600  IN  TXT  "v=DKIM1; k=rsa; p=MIIBIjAN..."

# ドメイン確認（Googleサーチコンソール等）
example.com.   3600  IN  TXT  "google-site-verification=abc123"</div>
<div class="dns-type-use"><strong>使用場面：</strong>SPF/DKIM/DMARCによるメール認証、ドメイン所有権確認、各種サービス設定。</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
  <span class="dns-record-type-badge dns-badge-NS">NS</span>
  <h3>NSレコード — ネームサーバー</h3>
</div>
<div class="dns-type-desc">ドメインまたはサブドメインの権威ネームサーバーを指定します。ゾーン頂点のNSレコードはドメインレジストラが管理します。サブドメインを別のDNSプロバイダーに委任する際にも使用します。</div>
<div class="dns-type-example">example.com.  86400  IN  NS  ns1.cloudflare.com.
example.com.  86400  IN  NS  ns2.cloudflare.com.

# サブドメインの委任
staging.example.com.  3600  IN  NS  ns1.otherprovider.com.</div>
<div class="dns-type-use"><strong>使用場面：</strong>DNSプロバイダー変更時、サブドメインのDNS管理を別プロバイダーに委任する場合。</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
  <span class="dns-record-type-badge dns-badge-SOA">SOA</span>
  <h3>SOAレコード — 権威開始（Start of Authority）</h3>
</div>
<div class="dns-type-desc">DNSゾーンの管理情報を格納します。プライマリネームサーバー、管理者メールアドレス、シリアル番号、リフレッシュ/リトライ/有効期限タイマーが含まれます。各ゾーンに必ず1つ存在します。通常はDNSプロバイダーが自動管理します。</div>
<div class="dns-type-example">example.com.  86400  IN  SOA  ns1.example.com. admin.example.com. (
                2025051601  ; シリアル番号 (YYYYMMDDnn)
                3600        ; リフレッシュ間隔 (1時間)
                900         ; リトライ間隔 (15分)
                604800      ; 有効期限 (7日)
                300 )       ; 最小TTL (5分)</div>
<div class="dns-type-use"><strong>使用場面：</strong>通常は自動管理。BINDやPowerDNS等の自己ホスト型DNSでシリアル番号やTTLを手動調整する場合。</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
  <span class="dns-record-type-badge dns-badge-SRV">SRV</span>
  <h3>SRVレコード — サービスロケーター</h3>
</div>
<div class="dns-type-desc">特定サービスのサーバー情報（サービス名・プロトコル・優先度・ウェイト・ポート・ターゲット）を指定します。書式：<code>_サービス._プロト.ホスト TTL IN SRV 優先度 ウェイト ポート ターゲット</code></div>
<div class="dns-type-example"># Microsoft Teams / Skype for Business
_sip._tls.example.com.             3600  IN  SRV  100 1 443  sipdir.online.lync.com.
_sipfederationtls._tcp.example.com. 3600  IN  SRV  100 1 5061 sipfed.online.lync.com.

# XMPP (Jabber)
_xmpp-client._tcp.example.com.    3600  IN  SRV  5 0 5222  xmpp.example.com.</div>
<div class="dns-type-use"><strong>使用場面：</strong>Microsoft 365（Teams/Lync）、VoIP、XMPP、サービスディスカバリーが必要なプロトコル全般。</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
  <span class="dns-record-type-badge dns-badge-CAA">CAA</span>
  <h3>CAAレコード — 認証局認可（Certification Authority Authorization）</h3>
</div>
<div class="dns-type-desc">ドメインに対してSSL/TLS証明書を発行できる認証局（CA）を制限します。不正な証明書発行を防ぎます。タグの種類：<code>issue</code>（単一ドメイン証明書）、<code>issuewild</code>（ワイルドカード証明書）、<code>iodef</code>（違反通知先）。</div>
<div class="dns-type-example">example.com.  3600  IN  CAA  0 issue     "letsencrypt.org"
example.com.  3600  IN  CAA  0 issuewild  "letsencrypt.org"
example.com.  3600  IN  CAA  0 issue      "digicert.com"
example.com.  3600  IN  CAA  0 iodef      "mailto:security@example.com"</div>
<div class="dns-type-use"><strong>使用場面：</strong>SSL証明書セキュリティ強化。PCI-DSS等のコンプライアンス要件にも対応。</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
  <span class="dns-record-type-badge dns-badge-PTR">PTR</span>
  <h3>PTRレコード — ポインター（逆引きDNS）</h3>
</div>
<div class="dns-type-desc">AレコードとIPアドレスとホスト名の対応を逆にしたものです。<code>in-addr.arpa</code>（IPv4）または<code>ip6.arpa</code>（IPv6）ゾーンに存在します。ドメインレジストラではなく、ISPまたはホスティングプロバイダーに設定を依頼します。メールサーバーの信頼性確保に重要です。</div>
<div class="dns-type-example"># IPv4逆引きDNS（93.184.216.34 → example.com）
34.216.184.93.in-addr.arpa.  3600  IN  PTR  mail.example.com.</div>
<div class="dns-type-use"><strong>使用場面：</strong>メールサーバー設定（スパム対策）、ネットワーク診断、コンプライアンス要件の充足。</div>
</div>

</div>

---

## TTL（有効期限）早見表

| TTL値  | 秒数     | 推奨場面 |
|--------|----------|----------|
| 300    | 5分      | 移行作業中 — 変更が素早く反映される |
| 900    | 15分     | テスト中や頻繁に変更する場合 |
| 3600   | 1時間    | 一般的なレコードの標準値 |
| 86400  | 24時間   | 安定したレコード（NS・SOA等） |
| 172800 | 48時間   | ほとんど変更しない安定したレコード |

**ヒント：** DNS移行の前にTTLを短く設定しておくと、変更が素早く世界中に伝播します。安定したら元の値に戻してください。

---

## よくあるDNSトラブルと対処法

**変更が反映されない場合**
DNSの伝播にはレコードのTTL時間がかかります。TTLが86400（24時間）の場合、最大24時間かかることがあります。[whatsmydns.net](https://www.whatsmydns.net)で世界各地の伝播状況を確認できます。

**メールがスパムに振り分けられる場合**
SPF・DKIM・DMARCのTXTレコードがすべて正しく設定されているか確認してください。メールサーバーの逆引きDNS（PTRレコード）が未設定の場合もスパム判定の原因になります。

**CNAMEが競合する場合**
同一ホスト名にCNAMEと他のレコードタイプを共存させることはできません。ゾーン頂点（@）ではALIAS/ANAMEレコード（Cloudflare、Route 53）またはAレコードを使用してください。

**ホスト変更後に証明書エラーが出る場合**
新しいホストのCAを許可するCAAレコードへの更新と、A/CNAMEレコードを新サーバーに向けた後に、新しい証明書を取得してください。

---

## 関連ツール

<div id="dns-crosslinks">
  <a class="dns-crosslink" href="/ja/tools/ip-address-info/">IPアドレス情報</a>
  <a class="dns-crosslink" href="/ja/tools/robots-txt-generator/">Robots.txt ジェネレーター</a>
  <a class="dns-crosslink" href="/ja/tools/htaccess-generator/">.htaccess ジェネレーター</a>
</div>

---

<div id="dns-freee-cta">
  <h3>freeeで業務効率をさらに向上させましょう</h3>
  <p>DNSや技術設定が整ったら、次は経理・会計の自動化にも取り組んでみませんか？freee会計はクラウド上で請求書発行・経費精算・確定申告をまとめて管理できる、フリーランス・中小企業向けの会計ソフトです。初回30日間無料でお試しいただけます。</p>
  <a class="dns-freee-btn" href="https://www.freee.co.jp/" target="_blank" rel="noopener">freeeを無料で試してみる</a>
</div>

</div>

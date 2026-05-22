---
title: "DNS Record Guide — Configuration Helper"
date: 2025-05-16
description: "Complete DNS record type reference with configuration examples. Generate DNS settings for GitHub Pages, Vercel, Google Workspace, and more. Copy records instantly."
categories: ["Free Tools"]
tags: ["Developer Tools", "Programming", "Free Tools"]
slug: "dns-record-guide"
ShowToc: false
cover:
  image: "/images/covers/dns-record-guide.png"
  alt: "DNS Record Guide"
---

<div id="dns-app">

<style>
#dns-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 900px;
margin: 0 auto;
color: #1a1a2e;
line-height: 1.6;
}
#dns-app *, #dns-app *::before, #dns-app *::after {
box-sizing: border-box;
}
#dns-app h2 {
font-size: 1.4rem;
font-weight: 700;
margin: 2rem 0 1rem;
color: #1a1a2e;
border-bottom: 2px solid #e0e7ff;
padding-bottom: 0.4rem;
}
#dns-app h3 {
font-size: 1.05rem;
font-weight: 600;
margin: 0 0 0.4rem;
color: #1a1a2e;
}

/* ---------- Config Generator ---------- */
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
grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
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

/* ---------- Results ---------- */
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

/* ---------- Reference Table ---------- */
#dns-reference-section {
margin-top: 2.5rem;
}
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

/* ---------- Cross-links ---------- */
#dns-crosslinks {
display: flex;
flex-wrap: wrap;
gap: 0.6rem;
margin-top: 2.5rem;
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

/* ---------- Responsive ---------- */
@media (max-width: 600px) {
#dns-preset-grid {
grid-template-columns: repeat(2, 1fr);
}
.dns-record-row {
grid-template-columns: 1fr 1fr;
grid-template-rows: auto auto auto;
}
.dns-copy-btn {
grid-column: 1 / -1;
width: 100%;
margin-top: 0.3rem;
}
}
</style>

## DNS Configuration Helper

Enter your domain name, choose a preset configuration, and get ready-to-use DNS records.

<div id="dns-config-generator">
<label for="dns-domain-input">Your Domain Name</label>
<input type="text" id="dns-domain-input" placeholder="example.com" autocomplete="off" spellcheck="false" />

<label style="margin-bottom:0.5rem;">Configuration Preset</label>
<div id="dns-preset-grid">
<button class="dns-preset-btn dns-preset-active" data-preset="github-pages">GitHub Pages</button>
<button class="dns-preset-btn" data-preset="vercel">Vercel</button>
<button class="dns-preset-btn" data-preset="netlify">Netlify</button>
<button class="dns-preset-btn" data-preset="cloudflare">Cloudflare</button>
<button class="dns-preset-btn" data-preset="google-workspace">Google Workspace</button>
<button class="dns-preset-btn" data-preset="microsoft-365">Microsoft 365</button>
<button class="dns-preset-btn" data-preset="cdn-basic">CDN (Basic)</button>
<button class="dns-preset-btn" data-preset="email-basic">Email Only</button>
</div>

<button id="dns-generate-btn">Generate DNS Records</button>

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
{ type:"CNAME", host:"www",  value:"yourusername.github.io", ttl:"3600", note:"Replace 'yourusername' with your GitHub username" },
{ type:"TXT",   host:"@",    value:"v=spf1 -all", ttl:"3600", note:"Basic SPF — update if you send email from this domain" },
]
},
"vercel": {
label: "Vercel",
records: [
{ type:"A",     host:"@",    value:"76.76.21.21",      ttl:"3600", note:"Vercel global IP" },
{ type:"CNAME", host:"www",  value:"cname.vercel-dns.com", ttl:"3600", note:"Vercel CNAME for www" },
{ type:"TXT",   host:"@",    value:"v=spf1 -all",      ttl:"3600", note:"Basic SPF — update if you send email" },
]
},
"netlify": {
label: "Netlify",
records: [
{ type:"A",     host:"@",    value:"75.2.60.5",        ttl:"3600", note:"Netlify load balancer IP" },
{ type:"CNAME", host:"www",  value:"apex-loadbalancer.netlify.com", ttl:"3600", note:"Netlify www CNAME" },
{ type:"TXT",   host:"@",    value:"v=spf1 -all",      ttl:"3600", note:"Basic SPF" },
]
},
"cloudflare": {
label: "Cloudflare (Proxy)",
records: [
{ type:"A",     host:"@",    value:"192.0.2.1",        ttl:"auto", note:"Replace with your origin server IP; enable Cloudflare proxy (orange cloud)" },
{ type:"CNAME", host:"www",  value:"example.com",      ttl:"auto", note:"Replace 'example.com' with your domain; enable proxy" },
{ type:"TXT",   host:"@",    value:"v=spf1 include:_spf.mx.cloudflare.net ~all", ttl:"3600", note:"Cloudflare Email Routing SPF (if using Cloudflare Email)" },
{ type:"MX",    host:"@",    value:"route1.mx.cloudflare.net", ttl:"3600", note:"Cloudflare Email Routing MX #1 — Priority 13" },
{ type:"MX",    host:"@",    value:"route2.mx.cloudflare.net", ttl:"3600", note:"Cloudflare Email Routing MX #2 — Priority 30" },
{ type:"MX",    host:"@",    value:"route3.mx.cloudflare.net", ttl:"3600", note:"Cloudflare Email Routing MX #3 — Priority 2" },
]
},
"google-workspace": {
label: "Google Workspace",
records: [
{ type:"MX",  host:"@", value:"aspmx.l.google.com",        ttl:"3600", note:"Google MX — Priority 1 (highest)" },
{ type:"MX",  host:"@", value:"alt1.aspmx.l.google.com",   ttl:"3600", note:"Priority 5" },
{ type:"MX",  host:"@", value:"alt2.aspmx.l.google.com",   ttl:"3600", note:"Priority 5" },
{ type:"MX",  host:"@", value:"alt3.aspmx.l.google.com",   ttl:"3600", note:"Priority 10" },
{ type:"MX",  host:"@", value:"alt4.aspmx.l.google.com",   ttl:"3600", note:"Priority 10" },
{ type:"TXT", host:"@", value:"v=spf1 include:_spf.google.com ~all", ttl:"3600", note:"Google Workspace SPF" },
{ type:"TXT", host:"@", value:"google-site-verification=REPLACE_WITH_YOUR_CODE", ttl:"3600", note:"Domain verification — get your code from Google Admin" },
{ type:"CNAME", host:"mail", value:"ghs.google.com",        ttl:"3600", note:"Custom mail URL (mail.yourdomain.com)" },
{ type:"CNAME", host:"calendar", value:"ghs.google.com",    ttl:"3600", note:"Custom calendar URL" },
{ type:"CNAME", host:"drive",    value:"ghs.google.com",    ttl:"3600", note:"Custom drive URL" },
{ type:"TXT", host:"_dmarc", value:"v=DMARC1; p=quarantine; rua=mailto:dmarc@DOMAIN; pct=100", ttl:"3600", note:"DMARC policy — replace DOMAIN with your domain" },
]
},
"microsoft-365": {
label: "Microsoft 365",
records: [
{ type:"MX",   host:"@",           value:"DOMAIN-com.mail.protection.outlook.com", ttl:"3600", note:"Replace 'DOMAIN-com' with your domain (hyphens, no dots) from M365 Admin" },
{ type:"TXT",  host:"@",           value:"v=spf1 include:spf.protection.outlook.com -all", ttl:"3600", note:"Microsoft 365 SPF" },
{ type:"TXT",  host:"@",           value:"MS=msXXXXXXXX",  ttl:"3600", note:"Domain verification — get code from M365 Admin Center" },
{ type:"CNAME", host:"autodiscover", value:"autodiscover.outlook.com", ttl:"3600", note:"Outlook Autodiscover" },
{ type:"CNAME", host:"selector1._domainkey", value:"selector1-DOMAIN-com._domainkey.TENANT.onmicrosoft.com", ttl:"3600", note:"DKIM selector 1 — get exact value from M365 Admin" },
{ type:"CNAME", host:"selector2._domainkey", value:"selector2-DOMAIN-com._domainkey.TENANT.onmicrosoft.com", ttl:"3600", note:"DKIM selector 2" },
{ type:"TXT",  host:"_dmarc",      value:"v=DMARC1; p=reject; rua=mailto:dmarc@DOMAIN; pct=100", ttl:"3600", note:"DMARC — replace DOMAIN with your domain" },
{ type:"SRV",  host:"_sip._tls",   value:"100 1 443 sipdir.online.lync.com", ttl:"3600", note:"Teams / Skype for Business" },
{ type:"SRV",  host:"_sipfederationtls._tcp", value:"100 1 5061 sipfed.online.lync.com", ttl:"3600", note:"Teams federation" },
]
},
"cdn-basic": {
label: "CDN (Generic)",
records: [
{ type:"A",     host:"@",    value:"YOUR_ORIGIN_IP",  ttl:"3600", note:"Replace with your origin server IP" },
{ type:"CNAME", host:"www",  value:"cdn.example.com", ttl:"3600", note:"Replace with your CDN-provided CNAME" },
{ type:"CNAME", host:"static", value:"cdn.example.com", ttl:"3600", note:"Optional: static assets subdomain" },
{ type:"TXT",   host:"@",    value:"v=spf1 include:YOUR_MAIL_PROVIDER ~all", ttl:"3600", note:"Update SPF for your mail provider" },
{ type:"CAA",   host:"@",    value:"0 issue \"letsencrypt.org\"", ttl:"3600", note:"Allow Let's Encrypt to issue certificates" },
{ type:"CAA",   host:"@",    value:"0 issuewild \"letsencrypt.org\"", ttl:"3600", note:"Allow wildcard certificates from Let's Encrypt" },
]
},
"email-basic": {
label: "Email Only (Generic)",
records: [
{ type:"MX",  host:"@",      value:"mail.DOMAIN",     ttl:"3600", note:"Primary mail server — set priority 10" },
{ type:"A",   host:"mail",   value:"YOUR_MAIL_SERVER_IP", ttl:"3600", note:"Mail server A record" },
{ type:"TXT", host:"@",      value:"v=spf1 mx ~all",  ttl:"3600", note:"SPF: authorize your MX server" },
{ type:"TXT", host:"_dmarc", value:"v=DMARC1; p=none; rua=mailto:dmarc@DOMAIN; pct=100", ttl:"3600", note:"DMARC in monitor mode — change p=none to p=quarantine or p=reject after analysis" },
{ type:"PTR", host:"YOUR_MAIL_SERVER_IP", value:"mail.DOMAIN", ttl:"3600", note:"Reverse DNS — configure with your hosting provider" },
]
}
};

let selectedPreset = "github-pages";

const domainInput   = document.getElementById("dns-domain-input");
const presetBtns    = document.querySelectorAll(".dns-preset-btn");
const generateBtn   = document.getElementById("dns-generate-btn");
const results       = document.getElementById("dns-results");
const resultTitle   = document.getElementById("dns-result-title");
const recordList    = document.getElementById("dns-record-list");

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

function makeCopyable(text) {
return text;
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
<div class="dns-record-label">Host / Name</div>
<div class="dns-record-value">${escHtml(host)}</div>
</div>
<div>
<div class="dns-record-label">Value / Points To</div>
<div class="dns-record-value">${escHtml(value)}</div>
</div>
<div>
<div class="dns-record-label">TTL</div>
<div class="dns-record-value">${escHtml(rec.ttl)}</div>
</div>
<button class="dns-copy-btn" data-copy="${escAttr(copyText)}">Copy</button>
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
resultTitle.textContent = `DNS records for ${domain} — ${preset.label}`;
recordList.innerHTML = preset.records.map(r => buildRecordHTML(r, domain)).join("");
results.classList.add("dns-visible");

recordList.querySelectorAll(".dns-copy-btn").forEach(btn => {
btn.addEventListener("click", () => {
navigator.clipboard.writeText(btn.dataset.copy).then(() => {
btn.textContent = "Copied!";
btn.classList.add("copied");
setTimeout(() => { btn.textContent = "Copy"; btn.classList.remove("copied"); }, 2000);
});
});
});
});

// Auto-generate on Enter
domainInput.addEventListener("keydown", e => { if (e.key === "Enter") generateBtn.click(); });
})();
</script>

---

## DNS Record Type Reference

<div id="dns-reference-section">

<div class="dns-type-card">
<div class="dns-type-card-header">
<span class="dns-record-type-badge dns-badge-A">A</span>
<h3>A Record — IPv4 Address</h3>
</div>
<div class="dns-type-desc">Maps a hostname to an IPv4 address. The most fundamental DNS record — when someone visits your domain, the A record tells DNS which server IP to connect to.</div>
<div class="dns-type-example">example.com.    3600  IN  A  93.184.216.34
www.example.com. 3600  IN  A  93.184.216.34</div>
<div class="dns-type-use"><strong>Use when:</strong> Pointing your domain to a web server, mail server, or any IPv4 address.</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
<span class="dns-record-type-badge dns-badge-AAAA">AAAA</span>
<h3>AAAA Record — IPv6 Address</h3>
</div>
<div class="dns-type-desc">Maps a hostname to an IPv6 address. Functions identically to an A record but for modern IPv6 infrastructure. Recommended to add alongside A records for full dual-stack support.</div>
<div class="dns-type-example">example.com.  3600  IN  AAAA  2606:2800:220:1:248:1893:25c8:1946</div>
<div class="dns-type-use"><strong>Use when:</strong> Your server supports IPv6 (GitHub Pages, Cloudflare, most modern CDNs).</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
<span class="dns-record-type-badge dns-badge-CNAME">CNAME</span>
<h3>CNAME Record — Canonical Name</h3>
</div>
<div class="dns-type-desc">Creates an alias from one hostname to another. Instead of an IP, a CNAME points to another domain name. Cannot be used at the zone apex (@) in standard DNS — use ALIAS/ANAME or flatten at the registrar. The target must ultimately resolve to an A or AAAA record.</div>
<div class="dns-type-example">www.example.com.   3600  IN  CNAME  example.com.
blog.example.com.  3600  IN  CNAME  my-site.netlify.app.</div>
<div class="dns-type-use"><strong>Use when:</strong> Pointing subdomains to hosting providers (Vercel, Netlify, GitHub Pages www subdomain, CDN hostnames).</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
<span class="dns-record-type-badge dns-badge-MX">MX</span>
<h3>MX Record — Mail Exchanger</h3>
</div>
<div class="dns-type-desc">Specifies the mail servers responsible for receiving email for a domain. Multiple MX records can exist with different priority values — lower numbers = higher priority. The value must be a hostname (not an IP address).</div>
<div class="dns-type-example">example.com.  3600  IN  MX  1   aspmx.l.google.com.
example.com.  3600  IN  MX  5   alt1.aspmx.l.google.com.
example.com.  3600  IN  MX  10  alt2.aspmx.l.google.com.</div>
<div class="dns-type-use"><strong>Use when:</strong> Configuring email delivery — Google Workspace, Microsoft 365, Fastmail, ProtonMail, etc.</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
<span class="dns-record-type-badge dns-badge-TXT">TXT</span>
<h3>TXT Record — Text</h3>
</div>
<div class="dns-type-desc">Stores arbitrary text data. Widely used for domain verification, email authentication (SPF, DKIM, DMARC), and service-specific configuration. A domain can have multiple TXT records.</div>
<div class="dns-type-example"># SPF — authorize mail senders
example.com.   3600  IN  TXT  "v=spf1 include:_spf.google.com ~all"

# DMARC — email policy
_dmarc.example.com.  3600  IN  TXT  "v=DMARC1; p=reject; rua=mailto:dmarc@example.com"

# DKIM — signing key
selector._domainkey.example.com.  3600  IN  TXT  "v=DKIM1; k=rsa; p=MIIBIjAN..."

# Domain verification
example.com.   3600  IN  TXT  "google-site-verification=abc123"</div>
<div class="dns-type-use"><strong>Use when:</strong> SPF/DKIM/DMARC email authentication, domain ownership verification, service configuration.</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
<span class="dns-record-type-badge dns-badge-NS">NS</span>
<h3>NS Record — Name Server</h3>
</div>
<div class="dns-type-desc">Delegates a domain or subdomain to a set of authoritative name servers. NS records at the zone apex are set by your domain registrar. You can also delegate subdomains to different DNS providers using NS records.</div>
<div class="dns-type-example">example.com.  86400  IN  NS  ns1.cloudflare.com.
example.com.  86400  IN  NS  ns2.cloudflare.com.

# Subdomain delegation
staging.example.com.  3600  IN  NS  ns1.otherprovider.com.</div>
<div class="dns-type-use"><strong>Use when:</strong> Changing DNS providers, delegating subdomain DNS management to another provider.</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
<span class="dns-record-type-badge dns-badge-SOA">SOA</span>
<h3>SOA Record — Start of Authority</h3>
</div>
<div class="dns-type-desc">Contains administrative information about a DNS zone: primary name server, responsible party's email, serial number, and refresh/retry/expire timers. Every DNS zone must have exactly one SOA record. Usually managed automatically by your DNS provider.</div>
<div class="dns-type-example">example.com.  86400  IN  SOA  ns1.example.com. admin.example.com. (
2025051601  ; Serial (YYYYMMDDnn)
3600        ; Refresh (1 hour)
900         ; Retry (15 min)
604800      ; Expire (7 days)
300 )       ; Minimum TTL (5 min)</div>
<div class="dns-type-use"><strong>Use when:</strong> Typically auto-managed. Manually adjust serial/TTL values in self-hosted DNS (BIND, PowerDNS).</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
<span class="dns-record-type-badge dns-badge-SRV">SRV</span>
<h3>SRV Record — Service Locator</h3>
</div>
<div class="dns-type-desc">Specifies the location of servers for specific services, including the service name, protocol, priority, weight, port, and target. Format: <code>_service._proto.name TTL IN SRV priority weight port target</code>.</div>
<div class="dns-type-example"># Microsoft Teams / Skype for Business
_sip._tls.example.com.           3600  IN  SRV  100 1 443  sipdir.online.lync.com.
_sipfederationtls._tcp.example.com. 3600 IN SRV 100 1 5061 sipfed.online.lync.com.

# XMPP (Jabber)
_xmpp-client._tcp.example.com.  3600  IN  SRV  5 0 5222  xmpp.example.com.</div>
<div class="dns-type-use"><strong>Use when:</strong> Microsoft 365 (Teams/Lync), VoIP, XMPP, and any protocol requiring service discovery.</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
<span class="dns-record-type-badge dns-badge-CAA">CAA</span>
<h3>CAA Record — Certification Authority Authorization</h3>
</div>
<div class="dns-type-desc">Controls which Certificate Authorities (CAs) are permitted to issue SSL/TLS certificates for your domain. Prevents unauthorized certificate issuance. Three tag types: <code>issue</code> (single domain), <code>issuewild</code> (wildcard), <code>iodef</code> (violation reporting).</div>
<div class="dns-type-example">example.com.  3600  IN  CAA  0 issue       "letsencrypt.org"
example.com.  3600  IN  CAA  0 issuewild   "letsencrypt.org"
example.com.  3600  IN  CAA  0 issue       "digicert.com"
example.com.  3600  IN  CAA  0 iodef       "mailto:security@example.com"</div>
<div class="dns-type-use"><strong>Use when:</strong> Strengthening SSL certificate security, required by some compliance frameworks (PCI-DSS).</div>
</div>

<div class="dns-type-card">
<div class="dns-type-card-header">
<span class="dns-record-type-badge dns-badge-PTR">PTR</span>
<h3>PTR Record — Pointer (Reverse DNS)</h3>
</div>
<div class="dns-type-desc">The reverse of an A record — maps an IP address back to a hostname. Lives in the <code>in-addr.arpa</code> (IPv4) or <code>ip6.arpa</code> (IPv6) zones. Configured with your ISP or hosting provider, not your domain registrar. Critical for mail server reputation.</div>
<div class="dns-type-example"># IPv4 reverse DNS (34.216.184.93 → example.com)
34.216.184.93.in-addr.arpa.  3600  IN  PTR  mail.example.com.

# IPv6 reverse DNS
6.4.9.1.8.c.5.2.3.9.8.1.8.4.2.0.1.0.0.0.0.2.2.0.0.8.2.6.0.6.2.ip6.arpa.  3600  IN  PTR  example.com.</div>
<div class="dns-type-use"><strong>Use when:</strong> Setting up a mail server (anti-spam), network diagnostics, compliance requirements.</div>
</div>

</div>

---

## Quick TTL Reference

| TTL Value | Seconds | When to Use |
|-----------|---------|-------------|
| 300       | 5 min   | During migrations — propagates changes quickly |
| 900       | 15 min  | Active testing or frequent changes |
| 3600      | 1 hour  | Standard for most records |
| 86400     | 24 hours| Stable records (NS, SOA) |
| 172800    | 48 hours| Very stable, rarely-changed records |

**Tip:** Lower TTL before a planned migration so DNS changes propagate quickly. Raise it again once stable.

---

## Common DNS Troubleshooting

**Changes not propagating?** DNS propagation takes time equal to the record's TTL. If your TTL was 86400 (24h), you may wait up to 24 hours. Use [whatsmydns.net](https://www.whatsmydns.net) to check propagation status globally.

**Email going to spam?** Ensure SPF, DKIM, and DMARC TXT records are all configured. A missing PTR (reverse DNS) record on your mail server is also a common cause.

**CNAME conflict?** You cannot have a CNAME and any other record type for the same hostname. At the zone apex (@), use ALIAS/ANAME records (Cloudflare, Route 53) or A records directly.

**Certificate errors after moving hosts?** Update your CAA records to allow the new host's CA, and ensure A/CNAME records point to the new server before requesting a new certificate.

---

## Related Tools

<div id="dns-crosslinks">
<a class="dns-crosslink" href="/tools/ip-address-info/">IP Address Info</a>
<a class="dns-crosslink" href="/tools/robots-txt-generator/">Robots.txt Generator</a>
<a class="dns-crosslink" href="/tools/htaccess-generator/">.htaccess Generator</a>
</div>

</div>

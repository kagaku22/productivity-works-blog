---
title: "Meta Tag Generator — SEO & Open Graph Tags"
description: "Generate SEO-optimized meta tags for your website including title, description, and Open Graph tags. Free meta tag creator."
date: 2025-05-16
slug: "meta-tag-generator"
categories: ["Free Tools"]
ShowToc: false
aliases:
  - "/tools/meta-tag-generator/"
  - "/tools/meta-tag-generator/"
cover:
  image: "/images/covers/meta-tag-generator.png"
  alt: "Meta Tag Generator"
---

<style>
#meta-app *,
#meta-app *::before,
#meta-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#meta-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
color: #1e293b;
max-width: 860px;
margin: 0 auto;
padding: 0 0 2rem;
}
#meta-app h2 {
font-size: 1.15rem;
font-weight: 700;
color: #0f172a;
margin: 1.75rem 0 1rem;
padding-bottom: 0.4rem;
border-bottom: 2px solid #e2e8f0;
}
#meta-app .field {
margin-bottom: 1.1rem;
}
#meta-app label {
display: block;
font-size: 0.85rem;
font-weight: 600;
color: #374151;
margin-bottom: 0.3rem;
}
#meta-app input[type="text"],
#meta-app input[type="url"],
#meta-app select,
#meta-app textarea {
width: 100%;
padding: 0.55rem 0.75rem;
border: 1.5px solid #cbd5e1;
border-radius: 6px;
font-size: 0.93rem;
background: #fff;
color: #1e293b;
transition: border-color 0.18s;
outline: none;
}
#meta-app input[type="text"]:focus,
#meta-app input[type="url"]:focus,
#meta-app select:focus,
#meta-app textarea:focus {
border-color: #2563eb;
box-shadow: 0 0 0 3px rgba(37,99,235,0.12);
}
#meta-app textarea {
resize: vertical;
min-height: 72px;
}
#meta-app .counter {
font-size: 0.78rem;
margin-top: 0.25rem;
font-weight: 500;
transition: color 0.18s;
}
#meta-app .counter.ok   { color: #16a34a; }
#meta-app .counter.warn { color: #d97706; }
#meta-app .counter.over { color: #dc2626; }
#meta-app .row2 {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1rem;
}
#meta-app .row3 {
display: grid;
grid-template-columns: 1fr 1fr 1fr;
gap: 1rem;
}
@media (max-width: 580px) {
#meta-app .row2,
#meta-app .row3 { grid-template-columns: 1fr; }
}

/* SERP Preview */
#meta-app .serp-box {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 1.1rem 1.3rem;
margin-top: 0.5rem;
}
#meta-app .serp-url {
font-size: 0.82rem;
color: #16a34a;
margin-bottom: 0.18rem;
word-break: break-all;
}
#meta-app .serp-title {
font-size: 1.12rem;
color: #2563eb;
font-weight: 600;
cursor: pointer;
line-height: 1.3;
margin-bottom: 0.22rem;
word-break: break-word;
}
#meta-app .serp-desc {
font-size: 0.88rem;
color: #4b5563;
line-height: 1.5;
word-break: break-word;
}

/* Social Previews */
#meta-app .social-row {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1rem;
margin-top: 0.5rem;
}
@media (max-width: 580px) {
#meta-app .social-row { grid-template-columns: 1fr; }
}
#meta-app .social-card {
border: 1.5px solid #e2e8f0;
border-radius: 10px;
overflow: hidden;
background: #f8fafc;
}
#meta-app .social-card-header {
background: #e2e8f0;
padding: 0.45rem 0.8rem;
font-size: 0.78rem;
font-weight: 700;
color: #475569;
letter-spacing: 0.04em;
text-transform: uppercase;
}
#meta-app .social-img-placeholder {
background: #cbd5e1;
height: 130px;
display: flex;
align-items: center;
justify-content: center;
color: #94a3b8;
font-size: 0.82rem;
position: relative;
overflow: hidden;
}
#meta-app .social-img-placeholder img {
width: 100%;
height: 100%;
object-fit: cover;
display: none;
}
#meta-app .social-img-placeholder .placeholder-text { position: absolute; }
#meta-app .social-body {
padding: 0.6rem 0.8rem 0.7rem;
}
#meta-app .fb-card .social-domain {
font-size: 0.72rem;
color: #6b7280;
text-transform: uppercase;
margin-bottom: 0.2rem;
}
#meta-app .fb-card .social-title {
font-size: 0.9rem;
font-weight: 700;
color: #1e293b;
margin-bottom: 0.15rem;
line-height: 1.3;
}
#meta-app .fb-card .social-desc {
font-size: 0.78rem;
color: #6b7280;
line-height: 1.4;
}
#meta-app .tw-card-inner {
border-radius: 0 0 10px 10px;
overflow: hidden;
}
#meta-app .tw-card .social-body {
background: #fff;
border-top: 1px solid #e2e8f0;
}
#meta-app .tw-card .social-title {
font-size: 0.88rem;
font-weight: 700;
color: #0f172a;
margin-bottom: 0.15rem;
}
#meta-app .tw-card .social-desc {
font-size: 0.78rem;
color: #6b7280;
line-height: 1.4;
}
#meta-app .tw-card .social-domain {
font-size: 0.72rem;
color: #6b7280;
margin-top: 0.2rem;
}

/* Output */
#meta-app .output-box {
position: relative;
margin-top: 0.5rem;
}
#meta-app pre {
background: #0f172a;
color: #e2e8f0;
padding: 1.1rem 1.2rem;
border-radius: 8px;
font-size: 0.82rem;
line-height: 1.65;
overflow-x: auto;
white-space: pre-wrap;
word-break: break-word;
font-family: "Fira Code", "Cascadia Code", "Consolas", monospace;
}
#meta-app .copy-btn {
position: absolute;
top: 0.6rem;
right: 0.6rem;
background: #2563eb;
color: #fff;
border: none;
padding: 0.35rem 0.85rem;
border-radius: 5px;
font-size: 0.8rem;
font-weight: 600;
cursor: pointer;
transition: background 0.16s;
}
#meta-app .copy-btn:hover { background: #1d4ed8; }
#meta-app .copy-btn.copied { background: #16a34a; }

/* Related */
#meta-app .related-link {
margin-top: 2rem;
padding: 0.9rem 1.1rem;
background: #eff6ff;
border-left: 4px solid #2563eb;
border-radius: 0 6px 6px 0;
font-size: 0.92rem;
color: #1e293b;
}
#meta-app .related-link a {
color: #2563eb;
font-weight: 600;
text-decoration: none;
}
#meta-app .related-link a:hover { text-decoration: underline; }
</style>

<div id="meta-app">

<h2>Basic SEO Tags</h2>

<div class="field">
<label for="mg-title">Page Title <span style="font-weight:400;color:#6b7280;">(recommended: 50–60 chars)</span></label>
<input type="text" id="mg-title" placeholder="My Awesome Page Title" maxlength="100" oninput="mgUpdate()">
<div class="counter ok" id="cnt-title">0 / 60</div>
</div>

<div class="field">
<label for="mg-desc">Meta Description <span style="font-weight:400;color:#6b7280;">(recommended: 120–160 chars)</span></label>
<textarea id="mg-desc" placeholder="A concise description of the page that appears in search results." maxlength="300" oninput="mgUpdate()"></textarea>
<div class="counter ok" id="cnt-desc">0 / 160</div>
</div>

<div class="row2">
<div class="field">
<label for="mg-keywords">Keywords <span style="font-weight:400;color:#6b7280;">(comma-separated)</span></label>
<input type="text" id="mg-keywords" placeholder="seo, meta tags, generator" oninput="mgUpdate()">
</div>
<div class="field">
<label for="mg-author">Author</label>
<input type="text" id="mg-author" placeholder="Jane Doe" oninput="mgUpdate()">
</div>
</div>

<div class="row2">
<div class="field">
<label for="mg-robots-index">Indexing</label>
<select id="mg-robots-index" onchange="mgUpdate()">
<option value="index">index</option>
<option value="noindex">noindex</option>
</select>
</div>
<div class="field">
<label for="mg-robots-follow">Link Following</label>
<select id="mg-robots-follow" onchange="mgUpdate()">
<option value="follow">follow</option>
<option value="nofollow">nofollow</option>
</select>
</div>
</div>

<h2>Open Graph Tags</h2>

<div class="row2">
<div class="field">
<label for="mg-og-title">og:title</label>
<input type="text" id="mg-og-title" placeholder="Same as page title, or custom" oninput="mgUpdate()">
</div>
<div class="field">
<label for="mg-og-type">og:type</label>
<select id="mg-og-type" onchange="mgUpdate()">
<option value="website">website</option>
<option value="article">article</option>
<option value="product">product</option>
<option value="video.movie">video.movie</option>
<option value="music.song">music.song</option>
<option value="book">book</option>
</select>
</div>
</div>

<div class="field">
<label for="mg-og-desc">og:description</label>
<textarea id="mg-og-desc" placeholder="Description for social sharing." oninput="mgUpdate()"></textarea>
</div>

<div class="row2">
<div class="field">
<label for="mg-og-url">og:url (canonical URL)</label>
<input type="url" id="mg-og-url" placeholder="https://example.com/page" oninput="mgUpdate()">
</div>
<div class="field">
<label for="mg-og-image">og:image URL</label>
<input type="url" id="mg-og-image" placeholder="https://example.com/image.jpg" oninput="mgUpdate()">
</div>
</div>

<h2>Twitter Card Tags</h2>

<div class="row3">
<div class="field">
<label for="mg-tw-card">twitter:card</label>
<select id="mg-tw-card" onchange="mgUpdate()">
<option value="summary_large_image">summary_large_image</option>
<option value="summary">summary</option>
<option value="app">app</option>
<option value="player">player</option>
</select>
</div>
<div class="field">
<label for="mg-tw-title">twitter:title</label>
<input type="text" id="mg-tw-title" placeholder="Twitter-specific title" oninput="mgUpdate()">
</div>
<div class="field">
<label for="mg-tw-image">twitter:image URL</label>
<input type="url" id="mg-tw-image" placeholder="https://example.com/image.jpg" oninput="mgUpdate()">
</div>
</div>

<div class="field">
<label for="mg-tw-desc">twitter:description</label>
<textarea id="mg-tw-desc" placeholder="Description for Twitter sharing." oninput="mgUpdate()" style="min-height:56px;"></textarea>
</div>

<h2>Google SERP Preview</h2>
<div class="serp-box">
<div class="serp-url" id="prev-url">https://example.com/page</div>
<div class="serp-title" id="prev-title">Your Page Title</div>
<div class="serp-desc" id="prev-desc">Your meta description will appear here. Make it compelling and within 160 characters for best results.</div>
</div>

<h2>Social Share Preview</h2>
<div class="social-row">
<div class="social-card fb-card">
<div class="social-card-header">Facebook / Open Graph</div>
<div class="social-img-placeholder" id="fb-img-wrap">
<img id="fb-img" src="" alt="OG Image">
<span class="placeholder-text" id="fb-img-placeholder">og:image preview</span>
</div>
<div class="social-body">
<div class="social-domain" id="fb-domain">example.com</div>
<div class="social-title" id="fb-title">Your OG Title</div>
<div class="social-desc" id="fb-desc">og:description will appear here.</div>
</div>
</div>
<div class="social-card tw-card">
<div class="social-card-header">Twitter / X Card</div>
<div class="tw-card-inner">
<div class="social-img-placeholder" id="tw-img-wrap">
<img id="tw-img" src="" alt="Twitter Image">
<span class="placeholder-text" id="tw-img-placeholder">twitter:image preview</span>
</div>
<div class="social-body">
<div class="social-title" id="tw-title">Your Twitter Title</div>
<div class="social-desc" id="tw-desc">twitter:description will appear here.</div>
<div class="social-domain" id="tw-domain">example.com</div>
</div>
</div>
</div>
</div>

<h2>Generated HTML</h2>
<div class="output-box">
<pre id="mg-output"><!-- Fill in the form above to generate tags --></pre>
<button class="copy-btn" id="copy-btn" onclick="mgCopy()">Copy</button>
</div>

<div class="related-link">
Related: Generate favicons &rarr; <a href="/tools/favicon-generator/">Favicon Generator</a>
</div>

</div>

<script>
(function () {
function v(id) { return document.getElementById(id); }

function setCounter(elId, current, max) {
var el = v(elId);
el.textContent = current + " / " + max;
el.className = "counter";
if (current <= max * 0.8) el.classList.add("ok");
else if (current <= max) el.classList.add("warn");
else el.classList.add("over");
}

function esc(s) {
return s.replace(/&/g,"&amp;").replace(/"/g,"&quot;").replace(/</g,"&lt;").replace(/>/g,"&gt;");
}

function getDomain(url) {
try { return new URL(url).hostname || "example.com"; }
catch(e) { return url.replace(/^https?:\/\//,"").split("/")[0] || "example.com"; }
}

function updateImg(imgId, wrapId, phId, url) {
var img = v(imgId), wrap = v(wrapId), ph = v(phId);
if (url && url.trim()) {
img.src = url.trim();
img.style.display = "block";
ph.style.display = "none";
} else {
img.style.display = "none";
ph.style.display = "block";
}
}

window.mgUpdate = function () {
var title   = v("mg-title").value;
var desc    = v("mg-desc").value;
var kw      = v("mg-keywords").value;
var author  = v("mg-author").value;
var rIdx    = v("mg-robots-index").value;
var rFol    = v("mg-robots-follow").value;

var ogTitle = v("mg-og-title").value || title;
var ogDesc  = v("mg-og-desc").value || desc;
var ogType  = v("mg-og-type").value;
var ogUrl   = v("mg-og-url").value;
var ogImg   = v("mg-og-image").value;

var twCard  = v("mg-tw-card").value;
var twTitle = v("mg-tw-title").value || ogTitle;
var twDesc  = v("mg-tw-desc").value || ogDesc;
var twImg   = v("mg-tw-image").value || ogImg;

// Counters
setCounter("cnt-title", title.length, 60);
setCounter("cnt-desc", desc.length, 160);

// SERP Preview
v("prev-title").textContent = title || "Your Page Title";
v("prev-url").textContent   = ogUrl || "https://example.com/page";
v("prev-desc").textContent  = desc  || "Your meta description will appear here.";

// FB Preview
var domain = getDomain(ogUrl);
v("fb-domain").textContent = domain;
v("fb-title").textContent  = ogTitle || "Your OG Title";
v("fb-desc").textContent   = ogDesc  || "og:description will appear here.";
updateImg("fb-img","fb-img-wrap","fb-img-placeholder", ogImg);

// Twitter Preview
v("tw-domain").textContent = domain;
v("tw-title").textContent  = twTitle || "Your Twitter Title";
v("tw-desc").textContent   = twDesc  || "twitter:description will appear here.";
updateImg("tw-img","tw-img-wrap","tw-img-placeholder", twImg);

// Build output
var lines = [];
lines.push("<!-- Primary Meta Tags -->");
if (title)  lines.push('<meta name="title" content="' + esc(title) + '">');
if (desc)   lines.push('<meta name="description" content="' + esc(desc) + '">');
if (kw)     lines.push('<meta name="keywords" content="' + esc(kw) + '">');
if (author) lines.push('<meta name="author" content="' + esc(author) + '">');
lines.push('<meta name="robots" content="' + rIdx + ", " + rFol + '">');

lines.push("");
lines.push("<!-- Open Graph / Facebook -->");
lines.push('<meta property="og:type" content="' + esc(ogType) + '">');
if (ogUrl)   lines.push('<meta property="og:url" content="' + esc(ogUrl) + '">');
if (ogTitle) lines.push('<meta property="og:title" content="' + esc(ogTitle) + '">');
if (ogDesc)  lines.push('<meta property="og:description" content="' + esc(ogDesc) + '">');
if (ogImg)   lines.push('<meta property="og:image" content="' + esc(ogImg) + '">');

lines.push("");
lines.push("<!-- Twitter Card -->");
lines.push('<meta property="twitter:card" content="' + esc(twCard) + '">');
if (ogUrl)   lines.push('<meta property="twitter:url" content="' + esc(ogUrl) + '">');
if (twTitle) lines.push('<meta property="twitter:title" content="' + esc(twTitle) + '">');
if (twDesc)  lines.push('<meta property="twitter:description" content="' + esc(twDesc) + '">');
if (twImg)   lines.push('<meta property="twitter:image" content="' + esc(twImg) + '">');

v("mg-output").textContent = lines.join("\n");
};

window.mgCopy = function () {
var text = v("mg-output").textContent;
if (!text || text.trim() === "<!-- Fill in the form above to generate tags -->") return;
navigator.clipboard.writeText(text).then(function () {
var btn = v("copy-btn");
btn.textContent = "Copied!";
btn.classList.add("copied");
setTimeout(function () {
btn.textContent = "Copy";
btn.classList.remove("copied");
}, 2000);
});
};

// Init
mgUpdate();
})();
</script>

---

## Related Tools

> [Html Beautifier](/tools/html-beautifier/)
> [Html Entity Converter](/tools/html-entity-converter/)
> [Html Entity Encoder](/tools/html-entity-encoder/)

## Related Articles

- [How to Use ChatGPT for Etsy Shop Descriptions (Complete 2026 Guide)](/posts/chatgpt-etsy-shop-descriptions/)
- [Etsy SEO: How to Generate Perfect Tags with ChatGPT (Step-by-Step)](/posts/etsy-seo-tags-chatgpt-optimization/)
- [Best Web Hosting 2026: Compared for Speed, Price & WordPress](/posts/best-web-hosting-2026/)

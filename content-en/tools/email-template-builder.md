---
title: "Email Template Builder"
description: "Create professional HTML email templates with a visual builder. Free responsive email template generator."
date: 2025-05-16
slug: "email-template-builder"
categories: ["Free Tools"]
ShowToc: false
aliases:
  - "/tools/html-email-builder/"
  - "/tools/email-generator/"
cover:
  image: "/images/covers/email-template-builder.png"
  alt: "Email Template Builder"
---

Build responsive, email-client-safe HTML email templates visually — with live preview, preset themes, and one-click HTML copy.

<div id="et-app">
<style>
#et-app *,#et-app *::before,#et-app *::after{box-sizing:border-box;margin:0;padding:0}
#et-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1e293b;background:#f1f5f9;min-height:100vh;padding:0}
#et-app .et-wrap{display:grid;grid-template-columns:340px 1fr;gap:0;min-height:600px;background:#f1f5f9}
#et-app .et-panel{background:#fff;border-right:1px solid #e2e8f0;overflow-y:auto;max-height:900px;padding:0}
#et-app .et-panel-header{padding:16px 18px;background:linear-gradient(135deg,#6366f1 0%,#8b5cf6 100%);color:#fff}
#et-app .et-panel-header h2{font-size:15px;font-weight:700;margin-bottom:2px}
#et-app .et-panel-header p{font-size:12px;opacity:.85}
#et-app .et-section{padding:14px 16px;border-bottom:1px solid #f1f5f9}
#et-app .et-section-title{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.08em;color:#94a3b8;margin-bottom:10px}
#et-app .et-field{margin-bottom:10px}
#et-app .et-field label{display:block;font-size:12px;font-weight:600;color:#475569;margin-bottom:4px}
#et-app .et-field input[type=text],#et-app .et-field input[type=url],#et-app .et-field textarea,#et-app .et-field select{width:100%;padding:7px 10px;border:1px solid #cbd5e1;border-radius:6px;font-size:13px;color:#1e293b;background:#fff;outline:none;transition:border .15s}
#et-app .et-field input[type=text]:focus,#et-app .et-field input[type=url]:focus,#et-app .et-field textarea:focus,#et-app .et-field select:focus{border-color:#6366f1;box-shadow:0 0 0 3px rgba(99,102,241,.12)}
#et-app .et-field textarea{resize:vertical;min-height:70px;font-family:inherit}
#et-app .et-color-row{display:flex;gap:8px;align-items:center}
#et-app .et-color-row input[type=color]{width:36px;height:34px;padding:2px;border:1px solid #cbd5e1;border-radius:6px;cursor:pointer;background:#fff;flex-shrink:0}
#et-app .et-color-row input[type=text]{flex:1}
#et-app .et-toggle-row{display:flex;align-items:center;gap:8px;margin-bottom:8px}
#et-app .et-toggle-row label{font-size:12px;font-weight:600;color:#475569;cursor:pointer}
#et-app .et-toggle{position:relative;width:34px;height:18px;flex-shrink:0}
#et-app .et-toggle input{opacity:0;width:0;height:0;position:absolute}
#et-app .et-toggle-slider{position:absolute;inset:0;background:#cbd5e1;border-radius:9px;transition:.2s;cursor:pointer}
#et-app .et-toggle-slider::before{content:'';position:absolute;width:12px;height:12px;left:3px;top:3px;background:#fff;border-radius:50%;transition:.2s}
#et-app .et-toggle input:checked+.et-toggle-slider{background:#6366f1}
#et-app .et-toggle input:checked+.et-toggle-slider::before{transform:translateX(16px)}
#et-app .et-presets{display:grid;grid-template-columns:1fr 1fr;gap:6px;margin-bottom:4px}
#et-app .et-preset-btn{padding:7px 6px;border:1.5px solid #e2e8f0;border-radius:7px;background:#f8fafc;font-size:11px;font-weight:600;color:#475569;cursor:pointer;text-align:center;transition:all .15s}
#et-app .et-preset-btn:hover{border-color:#6366f1;color:#6366f1;background:#eef2ff}
#et-app .et-preview-area{display:flex;flex-direction:column;overflow:hidden}
#et-app .et-preview-toolbar{display:flex;align-items:center;gap:8px;padding:12px 16px;background:#fff;border-bottom:1px solid #e2e8f0;flex-wrap:wrap}
#et-app .et-preview-toolbar span{font-size:12px;font-weight:600;color:#64748b}
#et-app .et-view-btn{padding:5px 12px;border:1.5px solid #e2e8f0;border-radius:6px;background:#f8fafc;font-size:12px;font-weight:600;color:#475569;cursor:pointer;transition:all .15s}
#et-app .et-view-btn.active,#et-app .et-view-btn:hover{background:#6366f1;border-color:#6366f1;color:#fff}
#et-app .et-copy-btn{margin-left:auto;padding:6px 16px;background:linear-gradient(135deg,#6366f1 0%,#8b5cf6 100%);color:#fff;border:none;border-radius:7px;font-size:12px;font-weight:700;cursor:pointer;transition:opacity .15s}
#et-app .et-copy-btn:hover{opacity:.88}
#et-app .et-preview-frame{flex:1;padding:20px;background:#e2e8f0;display:flex;justify-content:center;align-items:flex-start;overflow-y:auto;min-height:500px}
#et-app .et-preview-shell{background:#fff;border-radius:8px;box-shadow:0 4px 24px rgba(0,0,0,.13);overflow:hidden;transition:width .25s}
#et-app .et-preview-shell iframe{display:block;border:none;width:100%;height:700px}
#et-app .et-html-out{display:none;padding:16px;background:#0f172a;border-radius:8px;margin:16px;overflow:auto}
#et-app .et-html-out pre{font-family:'Courier New',monospace;font-size:11px;color:#94a3b8;white-space:pre-wrap;word-break:break-all}
#et-app .et-toast{position:fixed;bottom:24px;right:24px;padding:10px 20px;background:#10b981;color:#fff;border-radius:8px;font-size:13px;font-weight:600;box-shadow:0 4px 16px rgba(0,0,0,.18);z-index:9999;opacity:0;transform:translateY(8px);transition:all .25s;pointer-events:none}
#et-app .et-toast.show{opacity:1;transform:translateY(0)}
@media(max-width:700px){
  #et-app .et-wrap{grid-template-columns:1fr}
  #et-app .et-panel{max-height:none;border-right:none;border-bottom:1px solid #e2e8f0}
}
</style>

<div class="et-wrap">
  <!-- LEFT PANEL -->
  <div class="et-panel">
    <div class="et-panel-header">
      <h2>Email Template Builder</h2>
      <p>Build email-safe HTML with inline CSS</p>
    </div>

    <!-- PRESETS -->
    <div class="et-section">
      <div class="et-section-title">Preset Templates</div>
      <div class="et-presets">
        <button class="et-preset-btn" onclick="etApplyPreset('newsletter')">Newsletter</button>
        <button class="et-preset-btn" onclick="etApplyPreset('announcement')">Announcement</button>
        <button class="et-preset-btn" onclick="etApplyPreset('welcome')">Welcome Email</button>
        <button class="et-preset-btn" onclick="etApplyPreset('receipt')">Receipt / Order</button>
      </div>
    </div>

    <!-- HEADER -->
    <div class="et-section">
      <div class="et-section-title">Header</div>
      <div class="et-toggle-row">
        <label class="et-toggle"><input type="checkbox" id="et-show-logo" checked onchange="etUpdate()"><span class="et-toggle-slider"></span></label>
        <label for="et-show-logo">Show Logo</label>
      </div>
      <div class="et-field" id="et-logo-field">
        <label>Logo URL</label>
        <input type="url" id="et-logo-url" placeholder="https://example.com/logo.png" oninput="etUpdate()">
      </div>
      <div class="et-field">
        <label>Logo Alt Text</label>
        <input type="text" id="et-logo-alt" value="Company Logo" oninput="etUpdate()">
      </div>
      <div class="et-field">
        <label>Header Background</label>
        <div class="et-color-row">
          <input type="color" id="et-header-bg-pick" value="#6366f1" oninput="etSyncColor('header-bg')">
          <input type="text" id="et-header-bg" value="#6366f1" oninput="etSyncPick('header-bg');etUpdate()">
        </div>
      </div>
      <div class="et-field">
        <label>Header Text / Logo Padding</label>
        <input type="text" id="et-header-text" value="Your Company" oninput="etUpdate()">
      </div>
    </div>

    <!-- HERO IMAGE -->
    <div class="et-section">
      <div class="et-section-title">Hero Image</div>
      <div class="et-toggle-row">
        <label class="et-toggle"><input type="checkbox" id="et-show-hero" onchange="etUpdate()"><span class="et-toggle-slider"></span></label>
        <label for="et-show-hero">Show Hero Image</label>
      </div>
      <div class="et-field">
        <label>Hero Image URL</label>
        <input type="url" id="et-hero-url" placeholder="https://example.com/hero.jpg" oninput="etUpdate()">
      </div>
      <div class="et-field">
        <label>Hero Alt Text</label>
        <input type="text" id="et-hero-alt" value="Hero Image" oninput="etUpdate()">
      </div>
    </div>

    <!-- CONTENT -->
    <div class="et-section">
      <div class="et-section-title">Content</div>
      <div class="et-field">
        <label>Heading</label>
        <input type="text" id="et-heading" value="Welcome to Our Newsletter" oninput="etUpdate()">
      </div>
      <div class="et-field">
        <label>Body Text</label>
        <textarea id="et-body" oninput="etUpdate()">Thank you for subscribing! We're excited to share the latest updates, tips, and news with you. Stay tuned for great content coming your way.</textarea>
      </div>
    </div>

    <!-- CTA BUTTON -->
    <div class="et-section">
      <div class="et-section-title">CTA Button</div>
      <div class="et-toggle-row">
        <label class="et-toggle"><input type="checkbox" id="et-show-cta" checked onchange="etUpdate()"><span class="et-toggle-slider"></span></label>
        <label for="et-show-cta">Show Button</label>
      </div>
      <div class="et-field">
        <label>Button Text</label>
        <input type="text" id="et-cta-text" value="Read More" oninput="etUpdate()">
      </div>
      <div class="et-field">
        <label>Button URL</label>
        <input type="url" id="et-cta-url" value="https://example.com" oninput="etUpdate()">
      </div>
      <div class="et-field">
        <label>Button Color</label>
        <div class="et-color-row">
          <input type="color" id="et-btn-bg-pick" value="#6366f1" oninput="etSyncColor('btn-bg')">
          <input type="text" id="et-btn-bg" value="#6366f1" oninput="etSyncPick('btn-bg');etUpdate()">
        </div>
      </div>
      <div class="et-field">
        <label>Button Text Color</label>
        <div class="et-color-row">
          <input type="color" id="et-btn-color-pick" value="#ffffff" oninput="etSyncColor('btn-color')">
          <input type="text" id="et-btn-color" value="#ffffff" oninput="etSyncPick('btn-color');etUpdate()">
        </div>
      </div>
    </div>

    <!-- STYLE -->
    <div class="et-section">
      <div class="et-section-title">Style</div>
      <div class="et-field">
        <label>Font Family</label>
        <select id="et-font" onchange="etUpdate()">
          <option value="Arial, Helvetica, sans-serif">Arial (safe)</option>
          <option value="'Georgia', Times, serif">Georgia (serif)</option>
          <option value="'Trebuchet MS', sans-serif">Trebuchet MS</option>
          <option value="Verdana, Geneva, sans-serif">Verdana</option>
          <option value="'Courier New', Courier, monospace">Courier New (mono)</option>
        </select>
      </div>
      <div class="et-field">
        <label>Body Background</label>
        <div class="et-color-row">
          <input type="color" id="et-body-bg-pick" value="#f4f4f5" oninput="etSyncColor('body-bg')">
          <input type="text" id="et-body-bg" value="#f4f4f5" oninput="etSyncPick('body-bg');etUpdate()">
        </div>
      </div>
      <div class="et-field">
        <label>Card Background</label>
        <div class="et-color-row">
          <input type="color" id="et-card-bg-pick" value="#ffffff" oninput="etSyncColor('card-bg')">
          <input type="text" id="et-card-bg" value="#ffffff" oninput="etSyncPick('card-bg');etUpdate()">
        </div>
      </div>
      <div class="et-field">
        <label>Text Color</label>
        <div class="et-color-row">
          <input type="color" id="et-text-color-pick" value="#374151" oninput="etSyncColor('text-color')">
          <input type="text" id="et-text-color" value="#374151" oninput="etSyncPick('text-color');etUpdate()">
        </div>
      </div>
    </div>

    <!-- FOOTER -->
    <div class="et-section">
      <div class="et-section-title">Footer</div>
      <div class="et-field">
        <label>Footer Text</label>
        <textarea id="et-footer" oninput="etUpdate()">© 2025 Your Company. All rights reserved.
123 Main Street, City, Country
Unsubscribe | Privacy Policy</textarea>
      </div>
      <div class="et-field">
        <label>Footer Background</label>
        <div class="et-color-row">
          <input type="color" id="et-footer-bg-pick" value="#f9fafb" oninput="etSyncColor('footer-bg')">
          <input type="text" id="et-footer-bg" value="#f9fafb" oninput="etSyncPick('footer-bg');etUpdate()">
        </div>
      </div>
    </div>
  </div>

  <!-- RIGHT: PREVIEW -->
  <div class="et-preview-area">
    <div class="et-preview-toolbar">
      <span>Preview:</span>
      <button class="et-view-btn active" id="et-btn-desktop" onclick="etSetView('desktop')">Desktop (600px)</button>
      <button class="et-view-btn" id="et-btn-mobile" onclick="etSetView('mobile')">Mobile (320px)</button>
      <button class="et-view-btn" id="et-btn-html" onclick="etSetView('html')">HTML Output</button>
      <button class="et-copy-btn" onclick="etCopyHtml()">Copy HTML</button>
    </div>
    <div class="et-preview-frame" id="et-preview-frame">
      <div class="et-preview-shell" id="et-preview-shell" style="width:600px">
        <iframe id="et-iframe" sandbox="allow-same-origin"></iframe>
      </div>
    </div>
    <div class="et-html-out" id="et-html-out">
      <pre id="et-html-pre"></pre>
    </div>
  </div>
</div>

<div class="et-toast" id="et-toast">HTML copied to clipboard!</div>

<script>
(function(){
  var etCurrentView='desktop';
  var etHtml='';

  function v(id){return document.getElementById(id)}
  function val(id){return v(id)?v(id).value:''}
  function chk(id){return v(id)?v(id).checked:false}

  function etSyncColor(name){
    var pick=v('et-'+name+'-pick');
    var txt=v('et-'+name);
    if(pick&&txt)txt.value=pick.value;
    etUpdate();
  }
  window.etSyncColor=etSyncColor;

  function etSyncPick(name){
    var pick=v('et-'+name+'-pick');
    var txt=v('et-'+name);
    if(pick&&txt)pick.value=txt.value;
  }
  window.etSyncPick=etSyncPick;

  function escHtml(s){
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  function nl2br(s){
    return s.replace(/\n/g,'<br>');
  }

  function etBuildHtml(){
    var font=val('et-font');
    var bodyBg=val('et-body-bg');
    var cardBg=val('et-card-bg');
    var textColor=val('et-text-color');
    var headerBg=val('et-header-bg');
    var footerBg=val('et-footer-bg');
    var btnBg=val('et-btn-bg');
    var btnColor=val('et-btn-color');
    var heading=val('et-heading');
    var body=val('et-body');
    var footer=val('et-footer');
    var ctaText=val('et-cta-text');
    var ctaUrl=val('et-cta-url');
    var logoUrl=val('et-logo-url');
    var logoAlt=val('et-logo-alt');
    var headerText=val('et-header-text');
    var heroUrl=val('et-hero-url');
    var heroAlt=val('et-hero-alt');
    var showLogo=chk('et-show-logo');
    var showHero=chk('et-show-hero');
    var showCta=chk('et-show-cta');

    var headerContent='';
    if(showLogo&&logoUrl){
      headerContent='<img src="'+escHtml(logoUrl)+'" alt="'+escHtml(logoAlt)+'" style="max-height:50px;max-width:180px;display:block;margin:0 auto;">';
    } else {
      headerContent='<span style="font-size:22px;font-weight:700;color:#ffffff;letter-spacing:-.5px;">'+escHtml(headerText)+'</span>';
    }

    var heroBlock='';
    if(showHero&&heroUrl){
      heroBlock='<tr><td style="padding:0;"><img src="'+escHtml(heroUrl)+'" alt="'+escHtml(heroAlt)+'" style="display:block;width:100%;max-width:600px;height:auto;border:0;"></td></tr>';
    }

    var ctaBlock='';
    if(showCta){
      ctaBlock='<tr><td style="padding:28px 40px 0 40px;text-align:center;"><a href="'+escHtml(ctaUrl)+'" target="_blank" style="display:inline-block;padding:14px 36px;background:'+btnBg+';color:'+btnColor+';font-family:'+font+';font-size:15px;font-weight:700;text-decoration:none;border-radius:6px;mso-padding-alt:0;border:0;">'+escHtml(ctaText)+'</a></td></tr>';
    }

    var footerLines=footer.split('\n').map(function(l){return escHtml(l);}).join('<br>');

    return '<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">\n'+
'<html xmlns="http://www.w3.org/1999/xhtml">\n'+
'<head>\n'+
'<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">\n'+
'<meta name="viewport" content="width=device-width, initial-scale=1.0">\n'+
'<title>'+escHtml(heading)+'</title>\n'+
'</head>\n'+
'<body style="margin:0;padding:0;background-color:'+bodyBg+';font-family:'+font+';">\n'+
'<table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%" style="background-color:'+bodyBg+';min-width:100%;">\n'+
'  <tr>\n'+
'    <td align="center" style="padding:24px 0;">\n'+
'      <!-- Email container -->\n'+
'      <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="600" style="max-width:600px;width:100%;background-color:'+cardBg+';border-radius:8px;overflow:hidden;">\n'+
'        <!-- Header -->\n'+
'        <tr>\n'+
'          <td style="background-color:'+headerBg+';padding:24px 40px;text-align:center;">\n'+
            headerContent+'\n'+
'          </td>\n'+
'        </tr>\n'+
        heroBlock+'\n'+
'        <!-- Heading -->\n'+
'        <tr>\n'+
'          <td style="padding:36px 40px 0 40px;text-align:center;">\n'+
'            <h1 style="margin:0;font-family:'+font+';font-size:24px;font-weight:700;color:'+textColor+';line-height:1.3;">'+escHtml(heading)+'</h1>\n'+
'          </td>\n'+
'        </tr>\n'+
'        <!-- Body -->\n'+
'        <tr>\n'+
'          <td style="padding:20px 40px 32px 40px;">\n'+
'            <p style="margin:0;font-family:'+font+';font-size:15px;line-height:1.7;color:'+textColor+';">'+nl2br(escHtml(body))+'</p>\n'+
'          </td>\n'+
'        </tr>\n'+
        ctaBlock+'\n'+
'        <!-- Footer -->\n'+
'        <tr>\n'+
'          <td style="background-color:'+footerBg+';padding:24px 40px;text-align:center;border-top:1px solid #e5e7eb;">\n'+
'            <p style="margin:0;font-family:'+font+';font-size:12px;color:#9ca3af;line-height:1.7;">'+footerLines+'</p>\n'+
'          </td>\n'+
'        </tr>\n'+
'      </table>\n'+
'    </td>\n'+
'  </tr>\n'+
'</table>\n'+
'</body>\n'+
'</html>';
  }

  function etUpdate(){
    etHtml=etBuildHtml();
    var iframe=v('et-iframe');
    if(iframe){
      var doc=iframe.contentDocument||iframe.contentWindow.document;
      doc.open();doc.write(etHtml);doc.close();
    }
    var pre=v('et-html-pre');
    if(pre)pre.textContent=etHtml;
    var logoField=v('et-logo-field');
    if(logoField)logoField.style.display=chk('et-show-logo')?'block':'none';
  }
  window.etUpdate=etUpdate;

  function etSetView(view){
    etCurrentView=view;
    var shell=v('et-preview-shell');
    var frame=v('et-preview-frame');
    var htmlOut=v('et-html-out');
    var iframe=v('et-iframe');
    ['desktop','mobile','html'].forEach(function(n){
      var btn=v('et-btn-'+n);
      if(btn)btn.classList.toggle('active',n===view);
    });
    if(view==='html'){
      if(shell)shell.style.display='none';
      if(htmlOut)htmlOut.style.display='block';
    } else {
      if(shell)shell.style.display='';
      if(htmlOut)htmlOut.style.display='none';
      var w=view==='mobile'?320:600;
      if(shell)shell.style.width=w+'px';
      if(iframe){
        iframe.style.width='100%';
        iframe.style.height='700px';
      }
    }
  }
  window.etSetView=etSetView;

  function etCopyHtml(){
    if(!etHtml)return;
    if(navigator.clipboard){
      navigator.clipboard.writeText(etHtml).then(etShowToast);
    } else {
      var ta=document.createElement('textarea');
      ta.value=etHtml;ta.style.position='fixed';ta.style.opacity='0';
      document.body.appendChild(ta);ta.select();
      document.execCommand('copy');document.body.removeChild(ta);
      etShowToast();
    }
  }
  window.etCopyHtml=etCopyHtml;

  function etShowToast(){
    var t=v('et-toast');
    if(!t)return;
    t.classList.add('show');
    setTimeout(function(){t.classList.remove('show');},2200);
  }

  var presets={
    newsletter:{
      'et-header-bg':'#1d4ed8','et-body-bg':'#f0f4ff','et-card-bg':'#ffffff',
      'et-text-color':'#1e293b','et-btn-bg':'#1d4ed8','et-btn-color':'#ffffff',
      'et-footer-bg':'#f8fafc',
      'et-heading':'This Week in Tech','et-cta-text':'Read Full Story',
      'et-body':'Welcome to this week\'s edition! Here are the top stories we handpicked for you. From AI breakthroughs to productivity hacks — we\'ve got it all covered.',
      'et-footer':'© 2025 Tech Newsletter. All rights reserved.\nUnsubscribe | Manage Preferences',
      'et-header-text':'Tech Weekly','et-font':'Arial, Helvetica, sans-serif',
      'et-logo-url':'','et-hero-url':'','et-cta-url':'https://example.com',
      'et-show-logo':false,'et-show-hero':false,'et-show-cta':true
    },
    announcement:{
      'et-header-bg':'#dc2626','et-body-bg':'#fff7f7','et-card-bg':'#ffffff',
      'et-text-color':'#1f2937','et-btn-bg':'#dc2626','et-btn-color':'#ffffff',
      'et-footer-bg':'#fef2f2',
      'et-heading':'Important Announcement','et-cta-text':'Learn More',
      'et-body':'We have an exciting update to share with you. We\'ve been working hard behind the scenes and are thrilled to announce something that will change how you work.',
      'et-footer':'© 2025 Company Inc. | 456 Business Ave, City\nYou are receiving this because you opted in.',
      'et-header-text':'ANNOUNCEMENT','et-font':'Arial, Helvetica, sans-serif',
      'et-logo-url':'','et-hero-url':'','et-cta-url':'https://example.com',
      'et-show-logo':false,'et-show-hero':false,'et-show-cta':true
    },
    welcome:{
      'et-header-bg':'#059669','et-body-bg':'#f0fdf4','et-card-bg':'#ffffff',
      'et-text-color':'#1f2937','et-btn-bg':'#059669','et-btn-color':'#ffffff',
      'et-footer-bg':'#f9fafb',
      'et-heading':'Welcome aboard! 🎉','et-cta-text':'Get Started',
      'et-body':'We\'re so glad you\'re here! Your account has been created successfully. Click the button below to explore your dashboard and start enjoying all the features we have prepared for you.',
      'et-footer':'© 2025 YourApp. Need help? support@yourapp.com\nUnsubscribe | Privacy Policy',
      'et-header-text':'YourApp','et-font':'Arial, Helvetica, sans-serif',
      'et-logo-url':'','et-hero-url':'','et-cta-url':'https://example.com/dashboard',
      'et-show-logo':false,'et-show-hero':false,'et-show-cta':true
    },
    receipt:{
      'et-header-bg':'#374151','et-body-bg':'#f9fafb','et-card-bg':'#ffffff',
      'et-text-color':'#374151','et-btn-bg':'#374151','et-btn-color':'#ffffff',
      'et-footer-bg':'#f3f4f6',
      'et-heading':'Your Order Confirmation','et-cta-text':'View Order Details',
      'et-body':'Thank you for your purchase! Your order #12345 has been confirmed and is being processed.\n\nOrder Total: $49.00\nEstimated Delivery: 3-5 business days\n\nYou will receive a shipping notification once your order is on its way.',
      'et-footer':'© 2025 Shop Inc. | 789 Commerce St\nQuestions? Contact us at orders@shop.com',
      'et-header-text':'ORDER CONFIRMED','et-font':'Arial, Helvetica, sans-serif',
      'et-logo-url':'','et-hero-url':'','et-cta-url':'https://example.com/orders',
      'et-show-logo':false,'et-show-hero':false,'et-show-cta':true
    }
  };

  function etApplyPreset(name){
    var p=presets[name];
    if(!p)return;
    Object.keys(p).forEach(function(id){
      var el=v(id);
      if(!el)return;
      if(el.type==='checkbox'){el.checked=!!p[id];}
      else{el.value=p[id];}
    });
    // sync color pickers
    ['header-bg','body-bg','card-bg','text-color','btn-bg','btn-color','footer-bg'].forEach(function(n){
      var txt=v('et-'+n);var pick=v('et-'+n+'-pick');
      if(txt&&pick)pick.value=txt.value;
    });
    etUpdate();
  }
  window.etApplyPreset=etApplyPreset;

  // init
  etUpdate();
})();
</script>

---

### Related Tools
> Format HTML → [HTML Beautifier](/tools/html-beautifier/)
> Generate meta tags → [Meta Tag Generator](/tools/meta-tag-generator/)
</div>

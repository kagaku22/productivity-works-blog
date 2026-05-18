---
title: "メールテンプレートビルダー"
description: "ビジュアルビルダーでプロフェッショナルなHTMLメールテンプレートを作成。無料レスポンシブメールテンプレート生成ツール。"
date: 2025-04-02
slug: "email-template-builder"
categories: ["無料ツール"]
ShowToc: false
aliases:
  - "/ja/tools/email-template-builder/"
  - "/ja/tools/email-template-builder/"
cover:
  image: "/images/covers/email-template-builder-ja.png"
  alt: "メールテンプレートビルダー"
---

インラインCSSのメール安全なHTMLメールを、プレビューを見ながら視覚的に作成できます。プリセットテンプレートやワンクリックでのHTML出力コピーに対応。

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
  <!-- 左パネル -->
  <div class="et-panel">
    <div class="et-panel-header">
      <h2>メールテンプレートビルダー</h2>
      <p>インラインCSSのメール安全なHTMLを生成</p>
    </div>

    <!-- プリセット -->
    <div class="et-section">
      <div class="et-section-title">プリセットテンプレート</div>
      <div class="et-presets">
        <button class="et-preset-btn" onclick="etApplyPreset('newsletter')">ニュースレター</button>
        <button class="et-preset-btn" onclick="etApplyPreset('announcement')">お知らせ</button>
        <button class="et-preset-btn" onclick="etApplyPreset('welcome')">ウェルカム</button>
        <button class="et-preset-btn" onclick="etApplyPreset('receipt')">注文確認</button>
      </div>
    </div>

    <!-- ヘッダー -->
    <div class="et-section">
      <div class="et-section-title">ヘッダー</div>
      <div class="et-toggle-row">
        <label class="et-toggle"><input type="checkbox" id="et-show-logo" checked onchange="etUpdate()"><span class="et-toggle-slider"></span></label>
        <label for="et-show-logo">ロゴを表示</label>
      </div>
      <div class="et-field" id="et-logo-field">
        <label>ロゴ URL</label>
        <input type="url" id="et-logo-url" placeholder="https://example.com/logo.png" oninput="etUpdate()">
      </div>
      <div class="et-field">
        <label>ロゴ alt テキスト</label>
        <input type="text" id="et-logo-alt" value="会社ロゴ" oninput="etUpdate()">
      </div>
      <div class="et-field">
        <label>ヘッダー背景色</label>
        <div class="et-color-row">
          <input type="color" id="et-header-bg-pick" value="#6366f1" oninput="etSyncColor('header-bg')">
          <input type="text" id="et-header-bg" value="#6366f1" oninput="etSyncPick('header-bg');etUpdate()">
        </div>
      </div>
      <div class="et-field">
        <label>ヘッダーテキスト（ロゴなし時）</label>
        <input type="text" id="et-header-text" value="あなたの会社名" oninput="etUpdate()">
      </div>
    </div>

    <!-- ヒーロー画像 -->
    <div class="et-section">
      <div class="et-section-title">ヒーロー画像</div>
      <div class="et-toggle-row">
        <label class="et-toggle"><input type="checkbox" id="et-show-hero" onchange="etUpdate()"><span class="et-toggle-slider"></span></label>
        <label for="et-show-hero">ヒーロー画像を表示</label>
      </div>
      <div class="et-field">
        <label>画像 URL</label>
        <input type="url" id="et-hero-url" placeholder="https://example.com/hero.jpg" oninput="etUpdate()">
      </div>
      <div class="et-field">
        <label>画像 alt テキスト</label>
        <input type="text" id="et-hero-alt" value="ヒーロー画像" oninput="etUpdate()">
      </div>
    </div>

    <!-- コンテンツ -->
    <div class="et-section">
      <div class="et-section-title">コンテンツ</div>
      <div class="et-field">
        <label>見出し</label>
        <input type="text" id="et-heading" value="ニュースレターへようこそ" oninput="etUpdate()">
      </div>
      <div class="et-field">
        <label>本文テキスト</label>
        <textarea id="et-body" oninput="etUpdate()">ご登録いただきありがとうございます！最新情報やお役立ちコンテンツをお届けします。今後ともよろしくお願いいたします。</textarea>
      </div>
    </div>

    <!-- CTAボタン -->
    <div class="et-section">
      <div class="et-section-title">CTAボタン</div>
      <div class="et-toggle-row">
        <label class="et-toggle"><input type="checkbox" id="et-show-cta" checked onchange="etUpdate()"><span class="et-toggle-slider"></span></label>
        <label for="et-show-cta">ボタンを表示</label>
      </div>
      <div class="et-field">
        <label>ボタンテキスト</label>
        <input type="text" id="et-cta-text" value="詳しく見る" oninput="etUpdate()">
      </div>
      <div class="et-field">
        <label>ボタンリンク URL</label>
        <input type="url" id="et-cta-url" value="https://example.com" oninput="etUpdate()">
      </div>
      <div class="et-field">
        <label>ボタン背景色</label>
        <div class="et-color-row">
          <input type="color" id="et-btn-bg-pick" value="#6366f1" oninput="etSyncColor('btn-bg')">
          <input type="text" id="et-btn-bg" value="#6366f1" oninput="etSyncPick('btn-bg');etUpdate()">
        </div>
      </div>
      <div class="et-field">
        <label>ボタン文字色</label>
        <div class="et-color-row">
          <input type="color" id="et-btn-color-pick" value="#ffffff" oninput="etSyncColor('btn-color')">
          <input type="text" id="et-btn-color" value="#ffffff" oninput="etSyncPick('btn-color');etUpdate()">
        </div>
      </div>
    </div>

    <!-- スタイル -->
    <div class="et-section">
      <div class="et-section-title">スタイル設定</div>
      <div class="et-field">
        <label>フォント</label>
        <select id="et-font" onchange="etUpdate()">
          <option value="Arial, Helvetica, sans-serif">Arial（推奨）</option>
          <option value="'Georgia', Times, serif">Georgia（セリフ）</option>
          <option value="'Trebuchet MS', sans-serif">Trebuchet MS</option>
          <option value="Verdana, Geneva, sans-serif">Verdana</option>
          <option value="'Courier New', Courier, monospace">Courier New（等幅）</option>
        </select>
      </div>
      <div class="et-field">
        <label>メール背景色</label>
        <div class="et-color-row">
          <input type="color" id="et-body-bg-pick" value="#f4f4f5" oninput="etSyncColor('body-bg')">
          <input type="text" id="et-body-bg" value="#f4f4f5" oninput="etSyncPick('body-bg');etUpdate()">
        </div>
      </div>
      <div class="et-field">
        <label>カード背景色</label>
        <div class="et-color-row">
          <input type="color" id="et-card-bg-pick" value="#ffffff" oninput="etSyncColor('card-bg')">
          <input type="text" id="et-card-bg" value="#ffffff" oninput="etSyncPick('card-bg');etUpdate()">
        </div>
      </div>
      <div class="et-field">
        <label>文字色</label>
        <div class="et-color-row">
          <input type="color" id="et-text-color-pick" value="#374151" oninput="etSyncColor('text-color')">
          <input type="text" id="et-text-color" value="#374151" oninput="etSyncPick('text-color');etUpdate()">
        </div>
      </div>
    </div>

    <!-- フッター -->
    <div class="et-section">
      <div class="et-section-title">フッター</div>
      <div class="et-field">
        <label>フッターテキスト</label>
        <textarea id="et-footer" oninput="etUpdate()">© 2025 あなたの会社名. All rights reserved.
〒000-0000 東京都○○区○○町1-2-3
配信停止 | プライバシーポリシー</textarea>
      </div>
      <div class="et-field">
        <label>フッター背景色</label>
        <div class="et-color-row">
          <input type="color" id="et-footer-bg-pick" value="#f9fafb" oninput="etSyncColor('footer-bg')">
          <input type="text" id="et-footer-bg" value="#f9fafb" oninput="etSyncPick('footer-bg');etUpdate()">
        </div>
      </div>
    </div>
  </div>

  <!-- 右：プレビュー -->
  <div class="et-preview-area">
    <div class="et-preview-toolbar">
      <span>プレビュー:</span>
      <button class="et-view-btn active" id="et-btn-desktop" onclick="etSetView('desktop')">デスクトップ（600px）</button>
      <button class="et-view-btn" id="et-btn-mobile" onclick="etSetView('mobile')">モバイル（320px）</button>
      <button class="et-view-btn" id="et-btn-html" onclick="etSetView('html')">HTML出力</button>
      <button class="et-copy-btn" onclick="etCopyHtml()">HTMLをコピー</button>
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

<div class="et-toast" id="et-toast">HTMLをクリップボードにコピーしました!</div>

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
'      <!-- メールコンテナ -->\n'+
'      <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="600" style="max-width:600px;width:100%;background-color:'+cardBg+';border-radius:8px;overflow:hidden;">\n'+
'        <!-- ヘッダー -->\n'+
'        <tr>\n'+
'          <td style="background-color:'+headerBg+';padding:24px 40px;text-align:center;">\n'+
            headerContent+'\n'+
'          </td>\n'+
'        </tr>\n'+
        heroBlock+'\n'+
'        <!-- 見出し -->\n'+
'        <tr>\n'+
'          <td style="padding:36px 40px 0 40px;text-align:center;">\n'+
'            <h1 style="margin:0;font-family:'+font+';font-size:24px;font-weight:700;color:'+textColor+';line-height:1.3;">'+escHtml(heading)+'</h1>\n'+
'          </td>\n'+
'        </tr>\n'+
'        <!-- 本文 -->\n'+
'        <tr>\n'+
'          <td style="padding:20px 40px 32px 40px;">\n'+
'            <p style="margin:0;font-family:'+font+';font-size:15px;line-height:1.7;color:'+textColor+';">'+nl2br(escHtml(body))+'</p>\n'+
'          </td>\n'+
'        </tr>\n'+
        ctaBlock+'\n'+
'        <!-- フッター -->\n'+
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
      'et-heading':'今週のテックニュース','et-cta-text':'続きを読む',
      'et-body':'今週号をお届けします！AIの最新動向から仕事効率化のヒントまで、厳選した情報をまとめました。ぜひご一読ください。',
      'et-footer':'© 2025 テックニュースレター. All rights reserved.\n配信停止 | 配信設定変更',
      'et-header-text':'Tech Weekly','et-font':'Arial, Helvetica, sans-serif',
      'et-logo-url':'','et-hero-url':'','et-cta-url':'https://example.com',
      'et-show-logo':false,'et-show-hero':false,'et-show-cta':true
    },
    announcement:{
      'et-header-bg':'#dc2626','et-body-bg':'#fff7f7','et-card-bg':'#ffffff',
      'et-text-color':'#1f2937','et-btn-bg':'#dc2626','et-btn-color':'#ffffff',
      'et-footer-bg':'#fef2f2',
      'et-heading':'重要なお知らせ','et-cta-text':'詳細はこちら',
      'et-body':'平素より格別のご愛顧を賜り、誠にありがとうございます。このたび、重要なお知らせがございます。下記のボタンより詳細をご確認ください。',
      'et-footer':'© 2025 株式会社サンプル | 東京都渋谷区\n本メールにお心当たりのない場合はご連絡ください。',
      'et-header-text':'お知らせ','et-font':'Arial, Helvetica, sans-serif',
      'et-logo-url':'','et-hero-url':'','et-cta-url':'https://example.com',
      'et-show-logo':false,'et-show-hero':false,'et-show-cta':true
    },
    welcome:{
      'et-header-bg':'#059669','et-body-bg':'#f0fdf4','et-card-bg':'#ffffff',
      'et-text-color':'#1f2937','et-btn-bg':'#059669','et-btn-color':'#ffffff',
      'et-footer-bg':'#f9fafb',
      'et-heading':'ご登録ありがとうございます！','et-cta-text':'今すぐはじめる',
      'et-body':'アカウントの作成が完了しました。ダッシュボードからすべての機能をご利用いただけます。ご不明な点がございましたら、いつでもサポートまでお問い合わせください。',
      'et-footer':'© 2025 YourApp | サポート: support@yourapp.jp\n配信停止 | プライバシーポリシー',
      'et-header-text':'YourApp','et-font':'Arial, Helvetica, sans-serif',
      'et-logo-url':'','et-hero-url':'','et-cta-url':'https://example.com/dashboard',
      'et-show-logo':false,'et-show-hero':false,'et-show-cta':true
    },
    receipt:{
      'et-header-bg':'#374151','et-body-bg':'#f9fafb','et-card-bg':'#ffffff',
      'et-text-color':'#374151','et-btn-bg':'#374151','et-btn-color':'#ffffff',
      'et-footer-bg':'#f3f4f6',
      'et-heading':'ご注文の確認','et-cta-text':'注文詳細を確認する',
      'et-body':'この度はご注文いただきありがとうございます。ご注文番号 #12345 を承りました。\n\nご注文合計: ¥5,800\nお届け予定: 3〜5営業日以内\n\n発送準備が整い次第、配送通知メールをお送りします。',
      'et-footer':'© 2025 ショップ株式会社 | 東京都新宿区\nお問い合わせ: orders@shop.jp',
      'et-header-text':'注文確認','et-font':'Arial, Helvetica, sans-serif',
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
    ['header-bg','body-bg','card-bg','text-color','btn-bg','btn-color','footer-bg'].forEach(function(n){
      var txt=v('et-'+n);var pick=v('et-'+n+'-pick');
      if(txt&&pick)pick.value=txt.value;
    });
    etUpdate();
  }
  window.etApplyPreset=etApplyPreset;

  // 初期化
  etUpdate();
})();
</script>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

### 関連ツール
> HTMLを整形 → [HTML整形ツール](/ja/tools/html-beautifier/)
> メタタグ生成 → [メタタグ生成ツール](/ja/tools/meta-tag-generator/)

---
> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
</div>

## 関連記事

- [不動産営業向けChatGPTプロンプト集 完全ガイド2026](/ja/posts/chatgpt-fudosan-eigyo-prompt/)
- [不動産営業 ChatGPTで物件紹介メールを3分で作成する方法](/ja/posts/fudosan-eigyo-chatgpt-bukken-shoukai-mail/)
- [医療事務向けChatGPT活用術 業務効率化10選](/ja/posts/iryo-jimu-chatgpt-2026/)

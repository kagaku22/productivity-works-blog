---
title: "IP Subnet Calculator"
date: 2025-05-16
description: "Free online IP subnet calculator. Calculate network address, broadcast, host range, and wildcard mask from any IPv4 address and CIDR notation."
categories: ["Free Tools"]
slug: "ip-subnet-calculator"
ShowToc: false
cover:
  image: "/images/covers/ip-subnet-calculator.png"
  alt: "IP Subnet Calculator"
---

Enter any IPv4 address and CIDR prefix (or subnet mask) to instantly calculate the full subnet breakdown — network address, broadcast, usable host range, wildcard mask, and more.

<div id="ip-app">
<style>
#ip-app *,#ip-app *::before,#ip-app *::after{box-sizing:border-box;margin:0;padding:0}
#ip-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;font-size:15px;color:#1e293b;max-width:780px;margin:0 auto}
#ip-app .ip-card{background:#fff;border:1.5px solid #e2e8f0;border-radius:12px;padding:24px;margin-bottom:20px}
#ip-app .ip-title{font-size:17px;font-weight:700;color:#0f172a;margin-bottom:16px;padding-bottom:10px;border-bottom:1px solid #e2e8f0}
#ip-app .ip-row{display:flex;gap:12px;align-items:flex-end;flex-wrap:wrap;margin-bottom:16px}
#ip-app label{display:block;font-size:13px;font-weight:600;color:#475569;margin-bottom:5px}
#ip-app input[type=text],#ip-app select{width:100%;padding:10px 13px;border:1.5px solid #cbd5e1;border-radius:8px;font-size:15px;color:#1e293b !important;color-scheme:light;background:#f8fafc;transition:border-color .2s}
#ip-app input[type=text]:focus,#ip-app select:focus{outline:none;border-color:#3b82f6;background:#fff}
#ip-app .ip-field{flex:1;min-width:160px}
#ip-app .ip-field-sm{flex:0 0 130px}
#ip-app input[type=range]{width:100%;accent-color:#3b82f6;cursor:pointer}
#ip-app .ip-slider-row{display:flex;align-items:center;gap:12px;margin-bottom:14px}
#ip-app .ip-slider-val{font-size:20px;font-weight:800;color:#3b82f6;min-width:40px;text-align:center}
#ip-app .ip-btn{padding:10px 26px;background:#3b82f6;color:#fff;border:none;border-radius:8px;font-size:15px;font-weight:700;cursor:pointer;transition:background .15s;white-space:nowrap}
#ip-app .ip-btn:hover{background:#2563eb}
#ip-app .ip-btn-clear{background:#64748b}
#ip-app .ip-btn-clear:hover{background:#475569}
#ip-app .ip-error{color:#dc2626;font-size:13px;padding:8px 12px;background:#fef2f2;border:1px solid #fecaca;border-radius:6px;margin-top:-8px;margin-bottom:8px;display:none}
#ip-app .ip-results{display:none}
#ip-app .ip-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:12px;margin-bottom:12px}
#ip-app .ip-stat{background:#f8fafc;border:1px solid #e2e8f0;border-radius:9px;padding:13px 15px}
#ip-app .ip-stat-label{font-size:12px;font-weight:600;color:#64748b;text-transform:uppercase;letter-spacing:.5px;margin-bottom:4px}
#ip-app .ip-stat-val{font-size:16px;font-weight:700;color:#0f172a;font-family:'Courier New',monospace;word-break:break-all}
#ip-app .ip-stat-sub{font-size:12px;color:#94a3b8;margin-top:2px}
#ip-app .ip-badge{display:inline-block;padding:2px 9px;border-radius:20px;font-size:12px;font-weight:700;margin-left:6px}
#ip-app .ip-badge-a{background:#dbeafe;color:#1d4ed8}
#ip-app .ip-badge-b{background:#ede9fe;color:#6d28d9}
#ip-app .ip-badge-c{background:#dcfce7;color:#15803d}
#ip-app .ip-badge-d{background:#fef9c3;color:#a16207}
#ip-app .ip-badge-e{background:#fee2e2;color:#b91c1c}
#ip-app .ip-badge-priv{background:#f0fdf4;color:#166534}
#ip-app .ip-badge-pub{background:#eff6ff;color:#1e40af}
#ip-app .ip-bin-box{background:#0f172a;border-radius:9px;padding:14px 16px;font-family:'Courier New',monospace;font-size:13px;line-height:1.9;overflow-x:auto;margin-bottom:12px}
#ip-app .ip-bin-row{display:flex;gap:6px;align-items:center;white-space:nowrap}
#ip-app .ip-bin-label{color:#94a3b8;min-width:80px;font-size:12px}
#ip-app .ip-net-bit{color:#34d399}
#ip-app .ip-host-bit{color:#f87171}
#ip-app .ip-dot{color:#64748b;margin:0 2px}
#ip-app .ip-bin-sep{color:#475569;margin:0 1px}
#ip-app .ip-mask-vis{display:flex;gap:3px;flex-wrap:wrap;margin-bottom:14px}
#ip-app .ip-mask-bit{width:20px;height:20px;border-radius:3px;display:flex;align-items:center;justify-content:center;font-size:10px;font-weight:700}
#ip-app .ip-mask-1{background:#3b82f6;color:#fff}
#ip-app .ip-mask-0{background:#e2e8f0;color:#94a3b8}
#ip-app .ip-mask-grp{display:flex;gap:3px}
#ip-app .ip-mask-sep{width:6px}
#ip-app table{width:100%;border-collapse:collapse;font-size:13px}
#ip-app th{background:#f1f5f9;color:#475569;font-weight:600;text-align:left;padding:8px 10px;border-bottom:1.5px solid #e2e8f0}
#ip-app td{padding:7px 10px;border-bottom:1px solid #f1f5f9;font-family:'Courier New',monospace}
#ip-app tr:last-child td{border-bottom:none}
#ip-app tr.ip-hl td{background:#eff6ff;font-weight:700}
#ip-app .ip-tbl-wrap{max-height:320px;overflow-y:auto;border:1px solid #e2e8f0;border-radius:8px}
#ip-app .ip-section-label{font-size:13px;font-weight:700;color:#64748b;text-transform:uppercase;letter-spacing:.5px;margin-bottom:10px}
#ip-app .ip-cross{margin-top:8px;font-size:13px;color:#64748b}
#ip-app .ip-cross a{color:#3b82f6;text-decoration:none}
#ip-app .ip-cross a:hover{text-decoration:underline}
@media(max-width:520px){
#ip-app .ip-bin-row{flex-direction:column;align-items:flex-start}
#ip-app .ip-stat-val{font-size:14px}
}
</style>

<div class="ip-card">
<div class="ip-title">IPv4 Subnet Calculator</div>
<div class="ip-row">
<div class="ip-field">
<label for="ip-addr">IP Address</label>
<input type="text" id="ip-addr" placeholder="e.g. 192.168.1.0" maxlength="18" autocomplete="off" spellcheck="false">
</div>
<div class="ip-field-sm">
<label for="ip-mask-sel">Subnet Mask</label>
<select id="ip-mask-sel"></select>
</div>
<div style="display:flex;gap:8px;padding-bottom:1px">
<button class="ip-btn" onclick="ipCalc()">Calculate</button>
<button class="ip-btn ip-btn-clear" onclick="ipReset()">Clear</button>
</div>
</div>

<div class="ip-section-label">CIDR Prefix Length</div>
<div class="ip-slider-row">
<span style="font-size:12px;color:#94a3b8">/0</span>
<input type="range" id="ip-cidr" min="0" max="32" value="24" oninput="ipSliderChange(this.value)">
<span style="font-size:12px;color:#94a3b8">/32</span>
<span class="ip-slider-val" id="ip-cidr-label">/24</span>
</div>

<div class="ip-section-label" style="margin-bottom:8px">Subnet Mask Bits</div>
<div class="ip-mask-vis" id="ip-mask-vis"></div>

<div class="ip-error" id="ip-error"></div>
</div>

<div class="ip-results" id="ip-results">

<div class="ip-card">
<div class="ip-title">
Subnet Results
<span id="ip-class-badge"></span>
<span id="ip-scope-badge"></span>
</div>
<div class="ip-grid" id="ip-grid"></div>
</div>

<div class="ip-card">
<div class="ip-title">Binary View</div>
<div class="ip-section-label">Network bits = <span style="color:#34d399">green</span> &nbsp; Host bits = <span style="color:#f87171">red</span></div>
<div class="ip-bin-box" id="ip-bin-box"></div>
</div>

<div class="ip-card">
<div class="ip-title">Common Subnet Reference Table</div>
<div class="ip-tbl-wrap">
<table id="ip-tbl">
<thead><tr><th>CIDR</th><th>Subnet Mask</th><th>Hosts</th><th>Wildcard</th></tr></thead>
<tbody id="ip-tbl-body"></tbody>
</table>
</div>
</div>

</div>

<script>
(function(){
var MASKS=[
[0,'0.0.0.0'],[1,'128.0.0.0'],[2,'192.0.0.0'],[3,'224.0.0.0'],
[4,'240.0.0.0'],[5,'248.0.0.0'],[6,'252.0.0.0'],[7,'254.0.0.0'],
[8,'255.0.0.0'],[9,'255.128.0.0'],[10,'255.192.0.0'],[11,'255.224.0.0'],
[12,'255.240.0.0'],[13,'255.248.0.0'],[14,'255.252.0.0'],[15,'255.254.0.0'],
[16,'255.255.0.0'],[17,'255.255.128.0'],[18,'255.255.192.0'],[19,'255.255.224.0'],
[20,'255.255.240.0'],[21,'255.255.248.0'],[22,'255.255.252.0'],[23,'255.255.254.0'],
[24,'255.255.255.0'],[25,'255.255.255.128'],[26,'255.255.255.192'],[27,'255.255.255.224'],
[28,'255.255.255.240'],[29,'255.255.255.248'],[30,'255.255.255.252'],[31,'255.255.255.254'],
[32,'255.255.255.255']
];

var sel=document.getElementById('ip-mask-sel');
MASKS.forEach(function(m){
var o=document.createElement('option');
o.value=m[0];
o.textContent='/'+m[0]+' — '+m[1];
if(m[0]===24)o.selected=true;
sel.appendChild(o);
});
sel.addEventListener('change',function(){
document.getElementById('ip-cidr').value=this.value;
ipSliderChange(this.value);
});

document.getElementById('ip-addr').addEventListener('keydown',function(e){
if(e.key==='Enter')ipCalc();
});

renderMaskVis(24);

window.ipSliderChange=function(v){
v=parseInt(v,10);
document.getElementById('ip-cidr-label').textContent='/'+v;
document.getElementById('ip-cidr').value=v;
sel.value=v;
renderMaskVis(v);
};

function renderMaskVis(prefix){
var el=document.getElementById('ip-mask-vis');
el.innerHTML='';
for(var g=0;g<4;g++){
var grp=document.createElement('div');
grp.className='ip-mask-grp';
for(var b=0;b<8;b++){
var bit=g*8+b;
var d=document.createElement('div');
d.className='ip-mask-bit '+(bit<prefix?'ip-mask-1':'ip-mask-0');
d.textContent=bit<prefix?'1':'0';
grp.appendChild(d);
}
el.appendChild(grp);
if(g<3){var sep=document.createElement('div');sep.className='ip-mask-sep';el.appendChild(sep);}
}
}

function parseIP(s){
var p=s.trim().split('.');
if(p.length!==4)return null;
var n=[];
for(var i=0;i<4;i++){
var x=parseInt(p[i],10);
if(isNaN(x)||x<0||x>255||p[i].trim()==='')return null;
n.push(x);
}
return n;
}

function ipToNum(oct){return((oct[0]<<24)|(oct[1]<<16)|(oct[2]<<8)|oct[3])>>>0;}
function numToIP(n){return [n>>>24,(n>>>16)&255,(n>>>8)&255,n&255].join('.');}

function toBin8(n){return ('00000000'+n.toString(2)).slice(-8);}

function detectClass(oct){
var f=oct[0];
if(f<128)return 'A';
if(f<192)return 'B';
if(f<224)return 'C';
if(f<240)return 'D';
return 'E';
}

function isPrivate(oct){
var a=oct[0],b=oct[1];
if(a===10)return true;
if(a===172&&b>=16&&b<=31)return true;
if(a===192&&b===168)return true;
if(a===127)return true;
if(a===169&&b===254)return true;
return false;
}

function formatLarge(n){
if(n>=1e9)return (n/1e9).toFixed(2).replace(/\.?0+$/,'')+'B';
if(n>=1e6)return (n/1e6).toFixed(2).replace(/\.?0+$/,'')+'M';
if(n>=1e3)return (n/1e3).toFixed(2).replace(/\.?0+$/,'')+'K';
return n.toString();
}

window.ipCalc=function(){
var ipStr=document.getElementById('ip-addr').value.trim();
var prefix=parseInt(document.getElementById('ip-cidr').value,10);
var errEl=document.getElementById('ip-error');
var resEl=document.getElementById('ip-results');

errEl.style.display='none';
resEl.style.display='none';

if(!ipStr){showErr('Please enter an IP address.');return;}
var oct=parseIP(ipStr);
if(!oct){showErr('Invalid IP address. Use dotted decimal format (e.g. 192.168.1.0).');return;}
if(isNaN(prefix)||prefix<0||prefix>32){showErr('CIDR prefix must be between 0 and 32.');return;}

var ipNum=ipToNum(oct);
var maskNum= prefix===0?0:(0xFFFFFFFF<<(32-prefix))>>>0;
var wildNum=(~maskNum)>>>0;
var netNum=(ipNum&maskNum)>>>0;
var bcastNum=(netNum|wildNum)>>>0;
var firstHost=prefix<31?(netNum+1)>>>0:netNum;
var lastHost=prefix<31?(bcastNum-1)>>>0:bcastNum;
var hostCount=prefix>=31?(prefix===32?1:2):Math.pow(2,32-prefix)-2;

var cls=detectClass(oct);
var priv=isPrivate(oct);

// badges
var clsBadgeMap={A:'ip-badge-a',B:'ip-badge-b',C:'ip-badge-c',D:'ip-badge-d',E:'ip-badge-e'};
document.getElementById('ip-class-badge').innerHTML='<span class="ip-badge '+clsBadgeMap[cls]+'">Class '+cls+'</span>';
document.getElementById('ip-scope-badge').innerHTML='<span class="ip-badge '+(priv?'ip-badge-priv':'ip-badge-pub')+'">'+(priv?'Private':'Public')+'</span>';

// grid
var grid=document.getElementById('ip-grid');
var stats=[
{label:'IP Address',val:numToIP(ipNum),sub:'Input address'},
{label:'Network Address',val:numToIP(netNum),sub:'First address in subnet'},
{label:'Broadcast Address',val:numToIP(bcastNum),sub:'Last address in subnet'},
{label:'Subnet Mask',val:numToIP(maskNum),sub:'Dotted decimal notation'},
{label:'Wildcard Mask',val:numToIP(wildNum),sub:'Inverse of subnet mask'},
{label:'CIDR Notation',val:numToIP(netNum)+'/'+prefix,sub:'Network/prefix'},
{label:'First Usable Host',val:prefix<=30?numToIP(firstHost):'N/A',sub:prefix===31?'Point-to-point link':prefix===32?'Host route':''},
{label:'Last Usable Host',val:prefix<=30?numToIP(lastHost):'N/A',sub:''},
{label:'Usable Hosts',val:hostCount>=0?hostCount.toLocaleString():'0',sub:hostCount>=1000?'(~'+formatLarge(hostCount)+')':''},
{label:'Total Addresses',val:Math.pow(2,32-prefix).toLocaleString(),sub:'Including net & broadcast'},
];
grid.innerHTML=stats.map(function(s){
return '<div class="ip-stat"><div class="ip-stat-label">'+s.label+'</div><div class="ip-stat-val">'+s.val+'</div>'+(s.sub?'<div class="ip-stat-sub">'+s.sub+'</div>':'')+'</div>';
}).join('');

// binary
var binBox=document.getElementById('ip-bin-box');
function renderBinRow(label,num,pref){
var bits=[];
for(var i=31;i>=0;i--){
var b=(num>>>i)&1;
var bitPos=31-i;
var cls2=pref!==undefined?(bitPos<pref?'ip-net-bit':'ip-host-bit'):'';
bits.push('<span class="'+cls2+'">'+b+'</span>');
if(i>0&&(i%8===0))bits.push('<span class="ip-bin-sep"> . </span>');
}
return '<div class="ip-bin-row"><span class="ip-bin-label">'+label+'</span><span>'+bits.join('')+'</span></div>';
}
binBox.innerHTML=[
renderBinRow('IP Address:',ipNum,prefix),
renderBinRow('Subnet Mask:',maskNum),
renderBinRow('Network:',netNum,prefix),
renderBinRow('Broadcast:',bcastNum,prefix),
].join('');

// reference table
var tbody=document.getElementById('ip-tbl-body');
var rows=[];
for(var p=8;p<=32;p++){
var m=p===0?0:(0xFFFFFFFF<<(32-p))>>>0;
var w=(~m)>>>0;
var h=p>=31?(p===32?1:2):Math.pow(2,32-p)-2;
var hl=p===prefix?' class="ip-hl"':'';
rows.push('<tr'+hl+'><td>/'+p+'</td><td>'+numToIP(m)+'</td><td>'+(h>0?h.toLocaleString():0)+'</td><td>'+numToIP(w)+'</td></tr>');
}
tbody.innerHTML=rows.join('');

// scroll highlighted row into view
setTimeout(function(){
var hlRow=tbody.querySelector('.ip-hl');
if(hlRow)hlRow.scrollIntoView({block:'nearest'});
},50);

resEl.style.display='block';
};

window.ipReset=function(){
document.getElementById('ip-addr').value='';
document.getElementById('ip-cidr').value=24;
document.getElementById('ip-mask-sel').value=24;
ipSliderChange(24);
document.getElementById('ip-error').style.display='none';
document.getElementById('ip-results').style.display='none';
};

function showErr(msg){
var e=document.getElementById('ip-error');
e.textContent=msg;
e.style.display='block';
}

renderMaskVis(24);
})();
</script>

</div>

---

> Check your IP → [IP Address Info](/tools/ip-address-info/)
> Convert bytes → [Byte Converter](/tools/byte-converter/)
> DNS records → [DNS Record Guide](/tools/dns-record-guide/)

[cs2-online.html](https://github.com/user-attachments/files/33837479/cs2-online.html)
<!DOCTYPE html><html lang="ro"><head><meta charset="utf-8"><meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover"><title>CS Browser Online</title>
<style>
:root{color-scheme:dark;--bg:#0e1116;--fg:#fff;--ct:#6ea8ff;--t:#f5a623}
html,body{margin:0;height:100%;background:var(--bg);color:var(--fg);overflow:hidden;font-family:"Segoe UI",Arial,sans-serif;user-select:none}
canvas{display:block}.h{position:fixed;pointer-events:none;text-shadow:0 0 4px #000}
#menu,#ov{position:fixed;inset:0;display:flex;align-items:center;justify-content:center;z-index:9}
#menu{background:radial-gradient(circle at 30% 20%,#2b3340,var(--bg) 70%)}#ov{background:#000a;display:none;cursor:pointer;flex-direction:column;text-align:center}
.box{width:min(640px,92vw);padding:26px;background:#0009;border:1px solid #fff2;border-radius:10px;max-height:94vh;overflow:auto}
h1{margin:0 0 6px;font-size:46px;letter-spacing:3px}h1 span{color:var(--t);font-size:20px;margin-left:10px}h3{margin:16px 0 8px;color:#aab;font-size:13px;letter-spacing:2px;text-transform:uppercase}
.row{display:flex;gap:10px;flex-wrap:wrap}.o{flex:1;min-width:130px;padding:12px;border:2px solid #fff2;border-radius:8px;background:#fff1;cursor:pointer;text-align:center;font-weight:600}
.o.on{border-color:var(--t);background:#f5a62333}.o small{display:block;font-weight:400;color:#bbb;margin-top:4px}
input{width:100%;box-sizing:border-box;padding:10px;margin-top:5px;background:#0006;border:1px solid #fff3;border-radius:6px;color:#fff;font-size:16px}
button{padding:14px 20px;background:var(--t);color:#111;border:0;border-radius:8px;font-size:18px;font-weight:800;cursor:pointer;margin-top:18px;width:100%}
.s{color:#9aa;font-size:12px;line-height:1.5;margin:10px 0 0}
#rad{left:16px;top:16px;border-radius:50%;border:2px solid #fff4}
#top{left:50%;top:10px;transform:translateX(-50%);display:flex;background:#000a;border-radius:6px;overflow:hidden;font-weight:700}
#top span,#top b{padding:6px 16px;font-size:22px}#ct{background:#2a4d8a}#tt{background:#8a5a14}#tm{min-width:60px;text-align:center}
#feed{right:16px;top:16px;text-align:right;font-size:15px}#feed div{background:#000a;padding:3px 8px;margin-bottom:3px;border:1px solid #fff3;border-radius:3px}
#hp{left:24px;bottom:20px;font-size:44px;font-weight:700}#am{right:24px;bottom:20px;font-size:44px;font-weight:700;text-align:right}#am small{font-size:18px;color:#bbb}
#wl{right:24px;bottom:84px;font-size:14px;color:#aaa;text-align:right}#wl b{color:var(--t)}
#msg{left:50%;top:26%;transform:translateX(-50%);font-size:34px;font-weight:700;text-align:center;white-space:nowrap}
#ch{left:50%;top:50%}#ch i{position:absolute;background:var(--c,#3f3);box-shadow:0 0 2px #000}
#hm{left:50%;top:50%;width:22px;height:22px;margin:-11px;opacity:0;font-size:26px;text-align:center;line-height:22px}
#fl{inset:0;background:radial-gradient(transparent 40%,#d00);opacity:0}
#hn{left:50%;bottom:140px;transform:translateX(-50%);font-size:20px;font-weight:700;color:#ffd24a}.pn{position:fixed;inset:0;display:none;align-items:center;justify-content:center;z-index:12;background:#000c}.dp{position:fixed;left:50%;top:50%;font-size:22px;font-weight:800;pointer-events:none;text-shadow:0 0 4px #000;transition:transform .85s,opacity .85s;z-index:7}.by{display:block;margin-top:6px;background:var(--t);color:#111;border-radius:4px;padding:3px;font-size:12px;font-weight:700}input[type=range]{padding:0}#buy{position:fixed;inset:0;display:none;align-items:center;justify-content:center;z-index:8;background:#000a}#mo{left:24px;bottom:84px;color:#8f8;font-size:22px;font-weight:700}#sco{inset:0;display:none;background:radial-gradient(circle at 50% 50%,transparent 24%,#000 25%)}#sco:after{content:"";position:absolute;left:0;right:0;top:50%;height:1px;background:#000}
</style></head><body>
<div id="menu"><div class="box"><h1>CS<span>BROWSER ONLINE</span></h1>
<label class="s">Nume jucător<input id="nm" maxlength="12" value="Player"></label>
<h3>Mod de joc</h3><div id="modes" class="row"></div>
<div id="oc" style="display:none"><label class="s">Cod cameră (același la toți jucătorii)<input id="cd" maxlength="10" value="meci1"></label></div>
<h3>Echipă</h3><div id="teams" class="row"></div><h3>Hartă</h3><div id="maps" class="row"></div>
<button id="go">START MECI</button><div class="row"><button class="bst" style="background:#444;color:#fff">SETĂRI</button><button class="binv" style="background:#444;color:#fff">CUTII &amp; SKINURI</button></div>
<p class="s">WASD · mouse · click stânga foc · click dreapta scop · B cumpără · 1/2/Q arme · R reîncărcare · G smoke · Space sărit · Shift mers încet · Ctrl ghemuit. Online: trimite linkul prietenului (invitat în artifact), amândoi introduceți același cod și aceeași hartă.</p></div></div>
<div id="buy"><div class="box"><h1 style="font-size:28px">CUMPĂRARE <span id="bm"></span></h1><div id="bl"></div><button id="bc">ÎNCHIDE (B)</button></div></div><div id="st" class="pn"><div class="box"><h1 style="font-size:28px">SETĂRI</h1><div id="sl"></div><button id="sx">ÎNAPOI</button></div></div><div id="inv" class="pn"><div class="box"><h1 style="font-size:28px">CUTII &amp; SKINURI <span id="co"></span></h1><button id="oc2">DESCHIDE CUTIE · 300 monede</button><div id="cr" class="s" style="font-size:15px;min-height:28px"></div><h3>Inventar (click = echipează)</h3><div id="il" class="row"></div><button id="ix">ÎNAPOI</button></div></div><div id="ov"><div class="box"><h1>PAUZĂ</h1><label class="s">Nume jucător<input id="nm2" maxlength="12"></label><h3>Controale</h3><div class="s" id="ctl" style="font-size:14px;color:#dde"></div><button id="rs">CONTINUĂ</button><button id="bb" style="background:#2a7a3a;color:#fff">CUMPĂRĂ ARME (B)</button><div class="row"><button class="bst" style="background:#444;color:#fff">SETĂRI</button><button class="binv" style="background:#444;color:#fff">CUTII &amp; SKINURI</button></div><button id="mn" style="background:#444;color:#fff">Meniu principal</button></div></div>
<canvas id="rad" class="h" width="150" height="150"></canvas>
<div id="top" class="h"><span id="ct">0</span><b id="tm">1:55</b><span id="tt">0</span></div>
<div id="feed" class="h"></div><div id="hp" class="h"></div><div id="am" class="h"></div><div id="wl" class="h"></div><div id="mo" class="h"></div><div id="hn" class="h"></div><div id="msg" class="h"></div>
<div id="ch" class="h"><i></i><i></i><i></i><i></i><i></i></div><div id="hm" class="h">✕</div><div id="fl" class="h"></div><div id="sco" class="h"></div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
const T=THREE,$=i=>document.getElementById(i);
let ST={sens:1,scs:1,fov:75,vol:1,vg:1,vs:.6,chs:7,cht:2,chg:4,chd:0,cho:1,chc:'#33ff33',dmg:1,shd:1};try{Object.assign(ST,JSON.parse(localStorage.getItem('csst')||'{}'))}catch(e){}
const SAVE=()=>{try{localStorage.setItem('csst',JSON.stringify(ST))}catch(e){}};
let WS={coins:300,inv:[],eq:{}};try{const x=JSON.parse(localStorage.getItem('csw')||'null');if(x)WS=x}catch(e){}
const saveW=()=>{try{localStorage.setItem('csw',JSON.stringify(WS))}catch(e){}};
const SK=[['Original',null,0],['Gheață',0x3a8bd5,0],['Sânge',0xb01818,0],['Toxic',0x3ac43a,0],['Violet Neon',0x8a3aff,1],['Aur',0xe8b923,2],['Carbon',0x2a2a33,0],['Roz Bubble',0xff6fb5,1],['Foc',0xff7a18,1],['Crom',0xd0d8e0,2],['Albastru Regal',0x1f3fbf,0],['Camuflaj',0x5a6b3a,0]];
const SETS=[['Mouse & vizualizare'],['sens','Sensibilitate',.2,3,.05],['scs','Sensibilitate scop',.3,2,.05],['fov','Câmp vizual (FOV)',60,110,1],['Sunet'],['vol','Volum general',0,1,.05],['vg','Volum arme',0,1.5,.05],['vs','Volum pași/efecte',0,1.5,.05],['Țintă (crosshair)'],['chs','Lungime',0,20,1],['cht','Grosime',1,6,1],['chg','Spațiu',0,15,1],['chd','Punct central (0/1)',0,1,1],['cho','Opacitate',.2,1,.05],['chc','Culoare','color'],['Altele'],['dmg','Afișează damage (0/1)',0,1,1],['shd','Umbre (0/1)',0,1,1]];
const MAPS=[
{n:'Dunes',d:'Orașul de gresie',s:0x9cc4e8,f:0xd9d6c8,g:0xe8d2a8,w:0xf0d8b0,h:0xc9a36a,palm:1,W:[[-12,-12,10,8,8],[14,-14,8,10,10,0xe6c797],[0,-24,8,4,12],[-24,6,6,14,7],[24,6,8,8,7,0xe6c797],[0,0,5,5,2.6],[8,10,2,2,1.2],[-8,14,2,2,1.2],[0,18,12,1,1.6],[-14,-26,6,1,1.4],[16,26,6,1,1.4],[0,-8,1.5,8,2.4]]},
{n:'Depot',d:'Depou industrial',s:0x8e9aa6,f:0x9aa2aa,g:0x8a8d90,w:0xb8bcc0,h:0x777777,W:[[-10,-10,12,3,3.2,0xb5442f],[10,-10,12,3,3.2,0x2f6aa8],[0,0,3,16,3.2,0x4a8a4a],[-20,10,3,12,3.2,0xc8902a],[20,10,3,12,3.2,0xb5442f],[-8,18,10,3,3.2,0x2f6aa8],[8,-22,10,3,3.2,0x4a8a4a],[-26,-18,4,4,5,0x777777],[26,-18,4,4,5,0x777777],[0,-30,8,3,6,0x888888],[0,28,8,3,6,0x888888],[-14,0,2,2,1.1,0x999999],[14,0,2,2,1.1,0x999999]]},
{n:'Frost',d:'Tabără înzăpezită',s:0xcfe0ee,f:0xe4edf5,g:0xf2f6fa,w:0xdfe9f2,h:0xb8c8d8,W:[[-14,-8,8,8,6],[14,8,8,8,6],[-14,16,6,6,4,0xcfdbe8],[14,-16,6,6,4,0xcfdbe8],[0,0,6,6,2.4],[0,-20,14,2,3],[0,20,14,2,3],[-28,0,2,16,5,0xcfdbe8],[28,0,2,16,5,0xcfdbe8],[-6,-26,2,2,1.2],[6,26,2,2,1.2]]}];
const MODES=[['solo','Solo vs boți','Antrenament',1],['1v1','1v1 online','2 jucători',2],['2v2','2v2 online','4 jucători',4]];
const WP=[
{n:'USP-S',p:0,s:1,m:2,d:35,r:.16,mag:12,res:36,sp:.0015,rec:.014,au:0,mz:-.5,f:4500,th:220,z:65},
{n:'Glock-18',p:200,s:1,m:2,d:28,r:.12,mag:20,res:60,sp:.002,rec:.011,au:0,mz:-.5,f:4200,th:240,z:65},
{n:'P250',p:300,s:1,m:2,d:38,r:.15,mag:13,res:26,sp:.0016,rec:.015,au:0,mz:-.5,f:4700,th:210,z:65,sc:1.05},
{n:'Five-SeveN',p:500,s:1,m:2,d:32,r:.14,mag:20,res:40,sp:.0014,rec:.012,au:0,mz:-.5,f:5200,th:260,z:65,sc:1.1},
{n:'Desert Eagle',p:700,s:1,m:2,d:63,r:.35,mag:7,res:35,sp:.001,rec:.04,au:0,mz:-.62,f:6500,th:110,z:62,sc:1.3,hm:5},
{n:'MP9',p:1250,s:0,m:4,d:26,r:.07,mag:30,res:120,sp:.003,rec:.006,au:1,mz:-.6,f:5000,th:170,z:60},
{n:'P90',p:2350,s:0,m:4,d:26,r:.07,mag:50,res:100,sp:.0028,rec:.005,au:1,mz:-.62,f:5500,th:160,z:60,sc:1.15},
{n:'FAMAS',p:2050,s:0,m:0,d:30,r:.09,mag:25,res:90,sp:.002,rec:.008,au:1,mz:-.84,f:6500,th:140,z:55,sc:.95},
{n:'AK-47',p:2700,s:0,m:1,d:36,r:.1,mag:30,res:90,sp:.0025,rec:.011,au:1,mz:-.9,f:6000,th:150,z:55},
{n:'M4A1-S',p:2900,s:0,m:0,d:33,r:.09,mag:25,res:75,sp:.002,rec:.008,au:1,mz:-.84,f:7000,th:130,z:55},
{n:'SSG 08',p:1700,s:0,m:3,d:88,r:1.25,mag:10,res:30,sp:.0005,rec:.025,au:0,mz:-1.1,f:8000,th:100,z:30,sn:1,sc:.9},
{n:'AWP',p:4750,s:0,m:3,d:115,r:1.3,mag:5,res:20,sp:.0004,rec:.03,au:0,mz:-1.2,f:9000,th:90,z:25,sn:1}];
let ms=0,mm=0,pref=0;
MODES.forEach((m,i)=>{const e=document.createElement('div');e.className='o'+(i?'':' on');e.innerHTML=m[1]+'<small>'+m[2]+'</small>';e.onclick=()=>{ms=i;[...$('modes').children].forEach((c,j)=>c.classList.toggle('on',j===i));$('oc').style.display=i?'block':'none'};$('modes').appendChild(e)});
MAPS.forEach((m,i)=>{const e=document.createElement('div');e.className='o'+(i?'':' on');e.style.background=`linear-gradient(#${m.s.toString(16).padStart(6,0)}88,#${m.g.toString(16).padStart(6,0)}88)`;e.innerHTML=m.n+'<small>'+m.d+'</small>';e.onclick=()=>{mm=i;[...$('maps').children].forEach((c,j)=>c.classList.toggle('on',j===i))};$('maps').appendChild(e)});

[['CT · Counter-Terrorists','Apărare · albastru'],['T · Terrorists','Atac · portocaliu']].forEach((m,i)=>{const e=document.createElement('div');e.className='o'+(i?'':' on');e.innerHTML=m[0]+'<small>'+m[1]+'</small>';e.onclick=()=>{pref=i;[...$('teams').children].forEach((c,j)=>c.classList.toggle('on',j===i))};$('teams').appendChild(e)});
const R=new T.WebGLRenderer({antialias:true});R.setSize(innerWidth,innerHeight);R.setPixelRatio(Math.min(devicePixelRatio,2));R.shadowMap.enabled=true;R.shadowMap.type=T.PCFSoftShadowMap;R.toneMapping=T.ACESFilmicToneMapping;R.toneMappingExposure=1.15;document.body.prepend(R.domElement);
const S=new T.Scene(),C=new T.PerspectiveCamera(75,innerWidth/innerHeight,.05,300);S.add(C);
const HL=new T.HemisphereLight(0xe6f0ff,0xc9a36a,.95);S.add(HL);const sun=new T.DirectionalLight(0xfff0cc,.85);sun.position.set(30,50,20);S.add(sun);sun.castShadow=!!ST.shd;sun.shadow.mapSize.set(2048,2048);const sc3=sun.shadow.camera;sc3.left=-65;sc3.right=65;sc3.top=65;sc3.bottom=-65;sc3.near=1;sc3.far=160;sun.shadow.bias=-.0004;
addEventListener('resize',()=>{R.setSize(innerWidth,innerHeight);C.aspect=innerWidth/innerHeight;C.updateProjectionMatrix()});
const cv=document.createElement('canvas');cv.width=cv.height=256;const cx=cv.getContext('2d');cx.scale(2,2);cx.fillStyle='#e6e6e6';cx.fillRect(0,0,128,128);
for(let i=0;i<900;i++){cx.fillStyle=`rgba(${Math.random()<.5?'60,60,60':'255,255,255'},${Math.random()*.12})`;cx.fillRect(Math.random()*128,Math.random()*128,2+Math.random()*4,2+Math.random()*4)}
cx.strokeStyle='rgba(60,50,40,.3)';cx.lineWidth=2;for(let y=0;y<128;y+=32){cx.beginPath();cx.moveTo(0,y);cx.lineTo(128,y);cx.stroke();for(let x=(y/32%2)*32;x<128;x+=64){cx.beginPath();cx.moveTo(x,y);cx.lineTo(x,y+32);cx.stroke()}}
const tex=(a,b)=>{const t=new T.CanvasTexture(cv);t.anisotropy=8;t.wrapS=t.wrapT=T.RepeatWrapping;t.repeat.set(a,b);return t};
const sc2=document.createElement('canvas');sc2.width=sc2.height=64;const sx=sc2.getContext('2d'),gr=sx.createRadialGradient(32,32,0,32,32,32);gr.addColorStop(0,'rgba(235,238,240,1)');gr.addColorStop(.6,'rgba(215,220,225,.8)');gr.addColorStop(1,'rgba(215,220,225,0)');sx.fillStyle=gr;sx.fillRect(0,0,64,64);const smokeTex=new T.CanvasTexture(sc2);

const boxes=[],wm=[];
function wall(x,z,w,d,h,c,tint){const m=new T.Mesh(new T.BoxGeometry(w,h,d),new T.MeshLambertMaterial({map:tex(Math.max(w,d)/4,h/4),color:c}));m.position.set(x,h/2,z);m.castShadow=m.receiveShadow=true;S.add(m);wm.push(m);boxes.push({x0:x-w/2,x1:x+w/2,z0:z-d/2,z1:z+d/2,h,edge:tint})}
function buildMap(M){S.background=new T.Color(M.s);S.fog=new T.Fog(M.f,30,120);HL.groundColor.setHex(M.h);
 const g=new T.Mesh(new T.PlaneGeometry(100,100),new T.MeshLambertMaterial({map:tex(25,25),color:M.g}));g.rotation.x=-Math.PI/2;g.receiveShadow=true;S.add(g);wm.push(g);
 wall(0,-40,82,2,12,M.w,1);wall(0,40,82,2,12,M.w,1);wall(-40,0,2,82,12,M.w,1);wall(40,0,2,82,12,M.w,1);M.W.forEach(w=>wall(w[0],w[1],w[2],w[3],w[4],w[5]||M.w));
 if(M.palm){const wo=new T.MeshLambertMaterial({color:0x7a5a30}),lf=new T.MeshLambertMaterial({color:0x4f7a2a});[[-8,-30],[18,-6],[-32,-20],[32,-32],[-20,34],[30,24]].forEach(([x,z])=>{const t=new T.Mesh(new T.CylinderGeometry(.25,.35,7,6),wo);t.position.set(x,3.5,z);S.add(t);for(let i=0;i<7;i++){const l=new T.Mesh(new T.ConeGeometry(.5,4,4),lf);l.position.set(x+Math.cos(i)*1.5,7.2,z+Math.sin(i)*1.5);l.rotation.set(Math.sin(i)*1.2,0,-Math.cos(i)*1.2);S.add(l)}})}}
function resolve(p,r,fy){for(const b of boxes){if(fy>=b.h-.3)continue;if(p.x>b.x0-r&&p.x<b.x1+r&&p.z>b.z0-r&&p.z<b.z1+r){const a=p.x-(b.x0-r),c=b.x1+r-p.x,d=p.z-(b.z0-r),e=b.z1+r-p.z,m=Math.min(a,c,d,e);if(m===a)p.x=b.x0-r;else if(m===c)p.x=b.x1+r;else if(m===d)p.z=b.z0-r;else p.z=b.z1+r}}}
function floorAt(p,fy){let h=0;for(const b of boxes)if(fy>=b.h-.3&&p.x>b.x0-.2&&p.x<b.x1+.2&&p.z>b.z0-.2&&p.z<b.z1+.2)h=Math.max(h,b.h);return h}

// ---- weapons ----
const mat=c=>new T.MeshPhongMaterial({color:c,shininess:70,specular:0x666666}),MT={dk:mat(0x2a2b30),bl:mat(0x111114),wd:mat(0x80501f),gl:mat(0x1b1b20),gd:mat(0x9a9aa2),gn:mat(0x4a5a3a),lens:mat(0x5599ff)};
const B=(g,w,h,d,x,y,z,m,rx)=>{const o=new T.Mesh(new T.BoxGeometry(w,h,d),MT[m]);o.position.set(x,y,z);if(rx)o.rotation.x=rx;g.add(o)};
const Cy=(g,r,l,x,y,z,m)=>{const o=new T.Mesh(new T.CylinderGeometry(r,r,l,12),MT[m]);o.rotation.x=Math.PI/2;o.position.set(x,y,z);g.add(o)};
function gun0(i){const g=new T.Group();
 if(i===0){B(g,.05,.08,.42,0,0,-.3,'dk');B(g,.04,.035,.16,0,.06,-.3,'bl');Cy(g,.013,.34,0,.015,-.68,'bl');Cy(g,.024,.14,0,.012,-.5,'dk');Cy(g,.02,.1,0,.012,-.8,'bl');B(g,.03,.11,.05,0,-.09,-.22,'bl',.15);B(g,.03,.08,.05,0,-.07,-.1,'bl',-.3);B(g,.04,.06,.2,0,-.01,0,'dk');B(g,.012,.04,.012,0,.05,-.72,'bl')}
 if(i===1){B(g,.05,.075,.4,0,0,-.3,'dk');B(g,.056,.06,.3,0,-.005,-.58,'wd');B(g,.05,.03,.2,0,.05,-.55,'wd');Cy(g,.012,.34,0,.03,-.78,'bl');Cy(g,.014,.3,0,.055,-.62,'gd');B(g,.03,.15,.06,0,-.1,-.32,'bl',.4);B(g,.03,.09,.05,0,-.08,-.12,'wd',-.3);B(g,.04,.08,.24,0,-.02,.02,'wd');B(g,.012,.045,.012,0,.06,-.85,'bl')}
 if(i===2){B(g,.04,.045,.24,0,.015,-.22,'gd');B(g,.035,.04,.2,0,-.02,-.2,'bl');B(g,.035,.11,.05,0,-.08,-.12,'bl',.2);Cy(g,.014,.12,0,.015,-.38,'bl');B(g,.01,.02,.01,0,.045,-.3,'bl')}
 if(i===3){B(g,.05,.08,.5,0,0,-.3,'gn');B(g,.045,.1,.28,0,-.01,.02,'gn');Cy(g,.016,.7,0,.02,-.85,'bl');Cy(g,.03,.34,0,.095,-.35,'bl');Cy(g,.038,.05,0,.095,-.19,'lens');Cy(g,.034,.05,0,.095,-.52,'lens');B(g,.03,.03,.06,.05,.03,-.2,'gd');B(g,.03,.08,.05,0,-.08,-.1,'gn',-.3)}
 if(i===4){B(g,.05,.08,.34,0,0,-.25,'dk');B(g,.04,.03,.2,0,.06,-.25,'bl');Cy(g,.014,.18,0,.015,-.5,'bl');B(g,.03,.14,.05,0,-.1,-.22,'bl');B(g,.03,.08,.05,0,-.07,-.08,'bl',-.3);B(g,.025,.05,.2,0,-.01,.08,'dk');B(g,.03,.05,.06,0,-.05,-.4,'gl')}
 return g}
function gun(i){const w=WP[i],g=gun0(w.m);g.scale.setScalar(w.sc||1);if(w.m!==2){B(g,.02,.02,.08,0,-.045,-.19,'bl');B(g,.032,.032,.04,0,.015,w.mz+.04,'bl');B(g,.055,.012,.12,0,.05,-.32,'gd')}else B(g,.03,.012,.07,0,-.04,-.15,'bl');g.traverse(o=>{if(o.isMesh&&[MT.dk,MT.gn,MT.wd,MT.gd].includes(o.material)){o.userData.sk=1;o.material=o.material.clone();o.userData.orig=o.material.color.getHex()}});return g}
function applySkins(){G.forEach((g,i)=>{const k=WS.eq[i]||0;g.traverse(o=>{if(o.userData.sk){o.material.color.setHex(k?SK[k][1]:o.userData.orig);o.material.emissive.setHex(k&&SK[k][2]===2?0x332200:0)}})})}
const vm=new T.Group();C.add(vm);const G=WP.map((w,i)=>{const g=gun(i);g.visible=!i;vm.add(g);return g});applySkins();
B(vm,.075,.075,.13,0,-.075,-.1,'gl');B(vm,.075,.075,.15,-.01,-.04,-.46,'gl');B(vm,.09,.09,.55,.1,-.2,.2,'gl',.45);B(vm,.09,.09,.55,-.12,-.15,-.1,'gl',.25);
const flash=new T.Mesh(new T.PlaneGeometry(.24,.24),new T.MeshBasicMaterial({color:0xffb84a,transparent:true,opacity:.95,depthWrite:false}));flash.visible=false;vm.add(flash);const fl2=new T.PointLight(0xffa040,0,9);vm.add(fl2);vm.position.set(.2,-.2,-.4);

// ---- audio ----
let AC,MX,RV;
function ac(){if(AC)return;AC=new(window.AudioContext||window.webkitAudioContext)();MX=AC.createGain();MX.gain.value=1.3*ST.vol;const cp=AC.createDynamicsCompressor();MX.connect(cp);cp.connect(AC.destination);RV=AC.createConvolver();const n=AC.sampleRate*1.4|0,b=AC.createBuffer(2,n,AC.sampleRate);for(let c=0;c<2;c++){const d=b.getChannelData(c);for(let i=0;i<n;i++)d[i]=(Math.random()*2-1)*Math.pow(1-i/n,2.5)}RV.buffer=b;const g=AC.createGain();g.gain.value=.3;RV.connect(g);g.connect(MX)}
function snd(o){if(!AC)return;let v=(o.v||1)*(o.s?ST.vs:1),pan=0;if(o.pos){const dx=o.pos.x-C.position.x,dz=o.pos.z-C.position.z,di=Math.hypot(dx,dz);v/=1+di/10;pan=Math.max(-1,Math.min(1,(dx*Math.cos(P.yaw)-dz*Math.sin(P.yaw))/(di||1)))}
 const t=AC.currentTime+(o.dl||0),n=AC.sampleRate*o.d|0,b=AC.createBuffer(1,n,AC.sampleRate),d=b.getChannelData(0);for(let i=0;i<n;i++)d[i]=(Math.random()*2-1)*Math.pow(1-i/n,o.k||3);
 const s=AC.createBufferSource();s.buffer=b;const f=AC.createBiquadFilter();f.type=o.ft||'lowpass';f.Q.value=o.q||1;f.frequency.setValueAtTime(o.f,t);f.frequency.exponentialRampToValueAtTime(Math.max(200,o.f/(o.e||6)),t+o.d);
 const g=AC.createGain();g.gain.value=Math.min(v,1)*.9;const p=AC.createStereoPanner();p.pan.value=pan;s.connect(f);f.connect(g);g.connect(p);p.connect(MX);if(o.d>.1)p.connect(RV);s.start(t);
 if(o.th){const os=AC.createOscillator(),og=AC.createGain();os.frequency.setValueAtTime(o.th,t);os.frequency.exponentialRampToValueAtTime(35,t+.13);og.gain.setValueAtTime(Math.min(v,1)*.8,t);og.gain.exponentialRampToValueAtTime(.001,t+.15);os.connect(og);og.connect(p);os.start(t);os.stop(t+.16)}}
const shotSnd=(w,pos,v)=>{const q=WP[w],big=q.sn||q.p>2000,r=.92+Math.random()*.16,vv=v*ST.vg;
snd({d:.03,f:5500*r,ft:'highpass',e:1,k:4,v:vv,pos});snd({d:big?.5:.3,f:q.f*r,th:q.th*r,k:2,v:vv,pos});snd({d:.25,f:700,th:q.th*.6,k:1.4,v:vv*.8,pos});
snd({d:big?.9:.55,f:1800,k:2.5,v:vv*.35,pos,dl:.1+Math.random()*.03});if(!big&&q.au)setTimeout(()=>snd({d:.04,f:9000,ft:'highpass',e:1,v:vv*.15,pos}),160+Math.random()*60)};

// ---- state ----
const k={};let locked=false,fire=false,zoom=false,running=false,online=false,started=false,need=1,code='',room=null,myId='',myName='Player',myTeam=0,mapM,ft=0,pt=0;
const P={pos:new T.Vector3(0,0,34),vx:0,vz:0,vy:0,yaw:0,pitch:0,rec:0,yk:0,hp:100,w:0,money:800,prim:-1,sec:0,am:WP.map(w=>w.mag),rs:WP.map(w=>w.res),rl:0,cd:0,og:true,burst:0,smk:2};
let bots=[],rem={},smokes=[],nades=[],fx=[],dead=false,over=false,freeze=999,timeLeft=115,s0=0,s1=0,rnd=0,flashT=0,banner='',fstep=0;
const rc=new T.Raycaster(),eye=new T.Vector3(),tgt=new T.Vector3(),tv=new T.Vector3();
addEventListener('keydown',e=>{k[e.code]=1;if(!running||e.target.tagName==='INPUT')return;if(e.code==='KeyR')reload();if(e.code==='KeyG')nade();if(e.code==='KeyB')toggleBuy();if(e.code==='KeyE')pickup();if(e.code==='Digit1'&&P.prim>=0)selW(P.prim);if(e.code==='Digit2')selW(P.sec);if(e.code==='KeyQ')selW(P.w===P.sec&&P.prim>=0?P.prim:P.sec)});addEventListener('keyup',e=>k[e.code]=0);
addEventListener('mousemove',e=>{if(!locked)return;const z=(zoom?WP[P.w].z/75*ST.scs:1)*ST.sens;P.yaw-=e.movementX*.0022*z;P.pitch=Math.max(-1.5,Math.min(1.5,P.pitch-e.movementY*.0022*z))});
addEventListener('mousedown',e=>{if(!locked)return;if(e.button===0){fire=true;if(!WP[P.w].au)shoot()}if(e.button===2&&!dead&&P.rl<=0)zoom=!zoom});addEventListener('mouseup',()=>fire=false);addEventListener('contextmenu',e=>e.preventDefault());
const CTL='<b>WASD</b> mișcare · <b>Mouse</b> țintire<br><b>Click stânga</b> foc · <b>Click dreapta</b> scop/zoom<br><b>R</b> reîncărcare · <b>G</b> grenadă smoke<br><b>B</b> meniu cumpărare (la început de rundă)<br><b>1</b> armă principală · <b>2</b> pistol · <b>Q</b> schimbă · <b>E</b> ridică arma<br><b>Space</b> sărit · <b>Shift</b> mers încet · <b>Ctrl</b> ghemuit<br><b>Esc</b> pauză / meniu';$('ctl').innerHTML=CTL;$('rs').onclick=()=>{myName=($('nm2').value||myName).slice(0,12);if(room)room.presence({n:myName});R.domElement.requestPointerLock()};$('mn').onclick=()=>location.reload();R.domElement.addEventListener('click',()=>{if(running&&!locked&&!buyOpen)R.domElement.requestPointerLock()});$('bc').onclick=()=>toggleBuy(false);
document.addEventListener('pointerlockchange',()=>{locked=document.pointerLockElement===R.domElement;if(running)$('ov').style.display=(locked||buyOpen)?'none':'flex';fire=false});

function addFx(o,t){S.add(o);fx.push({o,t})}
function line(a,b,c){addFx(new T.Line(new T.BufferGeometry().setFromPoints([a,b]),new T.LineBasicMaterial({color:c,transparent:true,opacity:.8})),.06)}
function feed(a,b){const d=document.createElement('div');d.innerHTML=a+' <span style="color:#aaa">☠</span> '+b;$('feed').appendChild(d);setTimeout(()=>d.remove(),5000)}
function selW(i){if(i===P.w||dead)return;P.w=i;G.forEach((g,j)=>g.visible=j===i);flash.position.set(0,.02,WP[i].mz-.08);fl2.position.set(0,.05,WP[i].mz);vm.position.y=-.42;P.rl=0;zoom=false;snd({d:.06,f:2500,v:.3})}
function mkChar(team){const g=new T.Group(),parts=[],lm=c=>new T.MeshLambertMaterial({color:c}),M={main:lm(1),vest:lm(1),helm:lm(1),skin:lm(1),pants:lm(1),boot:lm(0x111114),gear:lm(0x15151a),eye:lm(1)};
 const add=(w,h,d,x,y,z,m,ud)=>{const o=new T.Mesh(new T.BoxGeometry(w,h,d),M[m]);o.position.set(x,y,z);o.userData=Object.assign({},ud);o.castShadow=true;g.add(o);parts.push(o)},LG={leg:1},HD={head:1};
 add(.2,.46,.22,-.13,.64,0,'pants',LG);add(.2,.46,.22,.13,.64,0,'pants',LG);add(.19,.4,.21,-.13,.22,0,'pants',LG);add(.19,.4,.21,.13,.22,0,'pants',LG);add(.22,.12,.32,-.13,.06,-.03,'boot',LG);add(.22,.12,.32,.13,.06,-.03,'boot',LG);
 add(.52,.1,.3,0,.9,0,'gear');add(.52,.6,.3,0,1.22,0,'main');add(.55,.46,.34,0,1.25,0,'vest');add(.14,.12,.08,-.14,1.06,-.19,'gear');add(.14,.12,.08,.14,1.06,-.19,'gear');add(.14,.12,.08,0,1.06,-.19,'gear');
 add(.16,.1,.2,-.36,1.47,0,'vest');add(.16,.1,.2,.36,1.47,0,'vest');add(.13,.3,.13,-.37,1.28,0,'main');add(.13,.3,.13,.37,1.28,0,'main');
 add(.12,.12,.36,.2,1.16,-.22,'main');add(.12,.12,.36,-.1,1.13,-.34,'main');add(.1,.1,.1,.2,1.16,-.43,'gear');add(.1,.1,.1,-.1,1.13,-.55,'gear');
 add(.12,.08,.12,0,1.56,0,'skin');add(.24,.26,.24,0,1.7,0,'skin',HD);add(.3,.12,.3,0,1.84,0,'helm',HD);add(.2,.06,.02,0,1.72,-.125,'eye',HD);
 const gm=gun(team?8:9);gm.position.set(.14,1.1,-.08);g.add(gm);S.add(g);const c={g,parts,M,look:-1,hp:100,cd:1,seeT:0,av:0,avT:0,sd:1,sees:false};setLook(c,team);return c}
function setLook(c,t){c.look=t;const L=t?{main:0x6e5c3c,vest:0x3a3224,helm:0x24201a,skin:0x1c1c1e,pants:0x4a4234,eye:0xd9a77a}:{main:0x3a5c8f,vest:0x1d2535,helm:0x1c2a44,skin:0xd9a77a,pants:0x2a3040,eye:0x0a0a10};for(const k in L)c.M[k].color.setHex(L[k])}
function blocked(a,b){const d=b.clone().sub(a),L=d.length();rc.set(a,d.normalize());rc.far=L;return rc.intersectObjects(wm).length>0}
function smoked(a,b){const ab=b.clone().sub(a),l2=ab.lengthSq();for(const s of smokes){if(s.age<.8||s.age>s.life)continue;const t=Math.max(0,Math.min(1,s.p.clone().sub(a).dot(ab)/l2));if(a.clone().addScaledVector(ab,t).distanceTo(s.p)<3.6)return true}return false}
const peers=()=>room?room.peers().filter(p=>p.kind==='viewer'):[];
const ids=()=>peers().map(p=>p.peer).sort();const teamOf=id=>{const l=peers().slice().sort((a,b)=>a.peer<b.peer?-1:1),c=[0,0],cap=Math.max(1,need/2);for(const p of l){let t=p.presence.tm===1?1:0;if(c[t]>=cap)t=1-t;c[t]++;if(p.peer===id)return t}return 0};
const nameOf=id=>{const p=peers().find(p=>p.peer===id);return(p&&p.presence.n)||'Jucător'};

// ---- actions ----
function hurt(d,from){if(dead||over||freeze>0)return;P.hp-=d;flashT=.5;snd({d:.12,f:900,v:.7});if(P.hp<=0){P.hp=0;dead=true;fire=false;zoom=false;banner='Ai murit';if(!online){dropW(P.w,P.pos);setTimeout(()=>end(1-myTeam),1500)}if(online&&room){room.emit('kill',{k:from,w:P.w,x:P.pos.x,y:P.pos.y,z:P.pos.z});feed(nameOf(from),nameOf(myId))}}}
function reload(){const w=WP[P.w];if(P.rl>0||P.am[P.w]>=w.mag||P.rs[P.w]<=0||dead)return;P.rl=w.mag>12?2.1:1.6;zoom=false;snd({d:.05,f:3000,v:.4});setTimeout(()=>snd({d:.07,f:1800,v:.5,th:300}),P.rl*600)}
function shoot(){const w=WP[P.w];if(P.cd>0||P.rl>0||dead||freeze>0||over)return;if(P.am[P.w]<=0){reload();return}
 P.am[P.w]--;P.cd=w.r;const mv=Math.hypot(P.vx,P.vz),sp=w.sp+P.burst*.0022*(w.au?1:0)+mv*.0014+(P.og?0:.04)+(w.sn&&!zoom?.05:0);P.burst=Math.min(P.burst+1,12);
 C.updateMatrixWorld();const d=new T.Vector3((Math.random()-.5)*sp*2,(Math.random()-.5)*sp*2,-1).normalize().applyQuaternion(C.quaternion);
 rc.set(C.position,d);rc.far=200;const tg=wm.slice();bots.forEach(b=>tg.push(...b.parts));Object.values(rem).forEach(c=>{if(c.g.visible&&c.team!==myTeam)tg.push(...c.parts)});const h=rc.intersectObjects(tg)[0];
 P.rec+=w.rec+P.burst*.0007;P.yk+=(Math.random()-.5)*.005;vm.position.z+=.05+(w.sn?.08:0);vm.position.y+=.01;
 flash.visible=true;flash.rotation.z=Math.random()*6;fl2.intensity=1.6;ft=.04;shotSnd(P.w,null,1);
 const mz=new T.Vector3(.2,-.1,w.mz).applyMatrix4(C.matrixWorld),e2=h?h.point:C.position.clone().addScaledVector(d,120);line(mz,e2,0xffe090);
 if(online&&room)room.emit('shot',{x:P.pos.x,y:P.pos.y,z:P.pos.z,w:P.w});
 if(h){const o=h.object,ud=o.userData;if(ud.bot||ud.peer){const hs=ud.head,dm=hs?w.d*(w.hm||4):w.d*(ud.leg?.75:1);$('hm').style.opacity=1;$('hm').style.color=hs?'#f44':'#fff';setTimeout(()=>$('hm').style.opacity=0,120);snd({d:.04,f:3500,v:.4});dmgPop(dm,hs);
  if(ud.bot){const b=ud.bot;b.hp-=dm;if(b.hp<=0)killBot(b,hs)}else if(room)room.emit('hit',{to:ud.peer,d:dm})}
 else{const p=new T.Mesh(new T.SphereGeometry(.07,6,6),new T.MeshBasicMaterial({color:0x8a7a60,transparent:true}));p.position.copy(h.point);addFx(p,.25)}}
 if(w.sn)zoom=false}
function killBot(b,hs){dropW(b.wi,b.g.position);P.money=Math.min(16000,P.money+300);S.remove(b.g);bots=bots.filter(x=>x!==b);feed('<b style="color:var(--ct)">Tu</b>'+(hs?' 🎯':''),'<b style="color:var(--t)">Bot</b>');if(!bots.length)end(myTeam)}
function nade(){if(P.smk<=0||dead||freeze>0)return;P.smk--;C.updateMatrixWorld();const d=new T.Vector3(0,.25,-1).normalize().applyQuaternion(C.quaternion);const m=new T.Mesh(new T.SphereGeometry(.09,8,8),mat(0x667766));m.position.copy(C.position);S.add(m);nades.push({m,v:d.multiplyScalar(15),t:0})}
function popSmoke(p){const g=new T.Group(),mt=new T.SpriteMaterial({map:smokeTex,transparent:true,opacity:.95,depthWrite:false,fog:false}),sp=[];for(let i=0;i<20;i++){const s=new T.Sprite(mt);s.position.set(p.x+(Math.random()-.5)*3,.8+Math.random()*2.6,p.z+(Math.random()-.5)*3);s.scale.setScalar(.5);s.userData.tg=4.5+Math.random()*2;g.add(s);sp.push(s)}S.add(g);smokes.push({p:new T.Vector3(p.x,1.6,p.z),g,sp,mt,age:0,life:18});snd({d:.5,f:1200,v:.6,pos:p})}
function end(w){if(over)return;over=true;if(w===0)s0++;else s1++;P.money=Math.min(16000,P.money+((myTeam===w)?3250:1400));banner=(w===0?'Contra-teroriștii':'Teroriștii')+' câștigă runda';
 if(s0>=5||s1>=5){const win=(myTeam===(s0>=5?0:1)),g=win?400:150;WS.coins+=g;saveW();banner=(win?'🏆 Ai câștigat meciul!':'Ai pierdut meciul')+' · +'+g+' monede';setTimeout(()=>{s0=s1=0;rnd=0;P.money=800;P.prim=-1;P.sec=0;dead=false;newRound()},6500)}else setTimeout(newRound,3600)}
function newRound(){drops.forEach(d=>{S.remove(d.m);S.remove(d.ring)});drops=[];if(dead){P.prim=-1;P.sec=0}bots.forEach(b=>S.remove(b.g));bots=[];smokes.forEach(s=>S.remove(s.g));smokes=[];nades.forEach(n=>S.remove(n.m));nades=[];
 Object.assign(P,{vx:0,vz:0,vy:0,pitch:0,rec:0,yk:0,hp:100,rl:0,cd:0,burst:0,smk:2,am:WP.map(w=>w.mag),rs:WP.map(w=>w.res)});
 let idx=0;if(online){myTeam=teamOf(myId);idx=ids().filter(x=>teamOf(x)===myTeam).indexOf(myId)}else myTeam=pref;if(P.sec<=1)P.sec=myTeam?1:0;
 P.pos.set(-6+idx*12+(Math.random()-.5)*3,0,myTeam?-34:34);P.yaw=myTeam?Math.PI:0;
 if(!online)for(let i=0;i<3;i++){const b=mkChar(1-myTeam);b.wi=[8,9,7,5,2,4,10,1][Math.random()*8|0];b.parts.forEach(p=>p.userData.bot=b);b.g.position.set(-24+i*24+(Math.random()-.5)*4,0,myTeam?34:-34);bots.push(b)}
 dead=false;over=false;freeze=10;timeLeft=115;rnd++;banner='Runda '+rnd+' · B = cumpără';const tw=P.prim>=0?P.prim:P.sec;P.w=-1;selW(tw)}

// ---- update ----
function update(dt){
 const pe=peers();
 if(online&&!started){const m=room&&room.peers().find(p=>p.isMe&&p.sameTab);if(m)myId=m.peer;if(room&&myId&&pe.length>=need){started=true;newRound()}else banner=room?'Aștept jucători '+pe.length+'/'+need+' · cod: '+code:'Online indisponibil — deschide linkul ca membru/invitat';}
 if(started||!online){if(freeze>0){freeze-=dt;if(freeze<=0&&!over)banner=''}else if(!over){timeLeft-=dt;if(timeLeft<=0){timeLeft=0;end(0)}}}
 const w=WP[P.w];if(buyOpen&&(freeze<=0||dead))toggleBuy(false);P.cd-=dt;ft-=dt;if(ft<=0){flash.visible=false;fl2.intensity=0}
 if(P.rl>0){P.rl-=dt;if(P.rl<=0){const n=Math.min(w.mag-P.am[P.w],P.rs[P.w]);P.am[P.w]+=n;P.rs[P.w]-=n}}
 if(fire&&w.au&&!dead)shoot();else if(!fire)P.burst=Math.max(0,P.burst-dt*8);
 P.rec*=Math.exp(-dt*5);P.yk*=Math.exp(-dt*5);C.fov+=((zoom?WP[P.w].z:ST.fov)-C.fov)*Math.min(1,dt*14);C.updateProjectionMatrix();const scp=zoom&&WP[P.w].sn;$('sco').style.display=scp?'block':'none';vm.visible=!dead&&!scp;
 if(!dead){let f=(k.KeyW?1:0)-(k.KeyS?1:0),s=(k.KeyD?1:0)-(k.KeyA?1:0);if(freeze>0)f=s=0;
  const sp=k.ControlLeft?2.2:k.ShiftLeft?2.8:5.3,l=Math.hypot(f,s)||1,tx=(-Math.sin(P.yaw)*f+Math.cos(P.yaw)*s)/l*sp,tz=(-Math.cos(P.yaw)*f-Math.sin(P.yaw)*s)/l*sp,a=Math.min(1,dt*(P.og?14:2));
  P.vx+=(tx-P.vx)*a;P.vz+=(tz-P.vz)*a;P.pos.x+=P.vx*dt;P.pos.z+=P.vz*dt;resolve(P.pos,.4,P.pos.y);
  if(k.Space&&P.og&&freeze<=0){P.vy=5.6;P.og=false}P.vy-=16*dt;P.pos.y+=P.vy*dt;const fy=floorAt(P.pos,P.pos.y-P.vy*dt);if(P.pos.y<=fy&&P.vy<=0){P.pos.y=fy;P.vy=0;P.og=true}else if(P.pos.y>fy+.05)P.og=false;
  fstep-=dt*Math.hypot(P.vx,P.vz);if(fstep<=0&&P.og&&Math.hypot(P.vx,P.vz)>4){fstep=2;snd({d:.06,f:700,v:.25,k:2,s:1})}}
 const sm=Math.hypot(P.vx,P.vz),ey=dead?.3:(k.ControlLeft?1.2:1.65);
 C.position.set(P.pos.x,P.pos.y+ey+Math.sin(performance.now()/110)*.012*sm/5,P.pos.z);C.rotation.set(P.pitch+P.rec,P.yaw+P.yk,dead?.8:0,'YXZ');
 vm.position.x+=((zoom?.04:.2)+Math.sin(performance.now()/220)*.004*sm/5-vm.position.x)*Math.min(1,dt*10);vm.position.y+=((P.rl>0?-.3:zoom?-.12:-.2)-vm.position.y)*Math.min(1,dt*10);vm.position.z+=(-.4-vm.position.z)*Math.min(1,dt*14);vm.rotation.x=P.rl>0?-.7*Math.sin(Math.PI*(1-P.rl/1.9)):0;
 // network
 if(room&&started){pt-=dt;if(pt<=0){pt=.066;room.presence({n:myName,tm:pref,x:+P.pos.x.toFixed(2),y:+P.pos.y.toFixed(2),z:+P.pos.z.toFixed(2),yw:+P.yaw.toFixed(2),a:dead?0:1,r:rnd})}
  for(const p of pe){if(p.sameTab||p.isMe&&false)continue;if(p.isMe)continue;let c=rem[p.peer];if(!c)c=rem[p.peer]=mkChar(teamOf(p.peer)),c.parts.forEach(x=>x.userData.peer=p.peer);const q=p.presence;c.team=teamOf(p.peer);if(c.look!==c.team)setLook(c,c.team);
   if(q.x!==undefined){c.g.position.lerp(tv.set(q.x,q.y,q.z),Math.min(1,dt*14));c.g.rotation.y=q.yw;c.g.visible=q.a===1}
   eye.set(c.g.position.x,c.g.position.y+1.5,c.g.position.z);tgt.copy(C.position);c.sees=c.g.visible&&!smoked(eye,tgt)&&!blocked(eye,tgt)}
  if(!over&&freeze<=0){const a=[0,0],t=[0,0];for(const p of pe){const tm=teamOf(p.peer);t[tm]++;if(p.sameTab?!dead:(p.presence.r!==rnd||p.presence.a===1))a[tm]++}if(t[0]&&t[1]){if(!a[1])end(0);else if(!a[0])end(1)}}}
 // bots
 for(const b of bots){const p=b.g.position,dx=P.pos.x-p.x,dz=P.pos.z-p.z,dist=Math.hypot(dx,dz)||1;eye.set(p.x,1.5,p.z);tgt.set(P.pos.x,P.pos.y+1.4,P.pos.z);
  b.sees=!dead&&!over&&dist<90&&!smoked(eye,tgt)&&!blocked(eye,tgt);b.seeT=b.sees?b.seeT+dt:0;
  let dir=new T.Vector2(dx/dist,dz/dist),spd=0;
  if(freeze<=0&&!dead&&!over){if(b.sees&&dist<15){if(Math.random()<dt*.8)b.sd*=-1;dir.set(-dir.y*b.sd,dir.x*b.sd);spd=2.2}else spd=b.sees?3:4;
   if(b.avT>0){b.avT-=dt;dir.rotateAround(new T.Vector2(),b.av*1.4)}const px=p.x,pz=p.z;p.x+=dir.x*spd*dt;p.z+=dir.y*spd*dt;resolve(p,.4,0);if(Math.hypot(p.x-px,p.z-pz)<spd*dt*.4&&b.avT<=0){b.av=Math.random()<.5?1:-1;b.avT=1.2}}
  p.y=Math.abs(Math.sin(performance.now()/160+p.x))*.04*(spd>0);b.g.rotation.y=Math.atan2(-(b.sees?dx:dir.x),-(b.sees?dz:dir.y));
  b.cd-=dt;if(b.sees&&b.seeT>.45&&b.cd<=0&&freeze<=0&&!over){b.cd=.28+Math.random()*.15;const hit=Math.random()<Math.max(.08,.55-dist/70)*(sm>3?.6:1),m=new T.Vector3(p.x,1.3,p.z),e=tgt.clone();if(hit)hurt(Math.round(WP[b.wi].d*.35),'bot');else e.add(new T.Vector3((Math.random()-.5)*2,(Math.random()-.5)*1.4,(Math.random()-.5)*2));line(m,e,0xff9060);shotSnd(b.wi,p,.9)}}
 for(let i=nades.length-1;i>=0;i--){const n=nades[i];n.t+=dt;n.v.y-=18*dt;const o=n.m.position.clone();n.m.position.addScaledVector(n.v,dt);const q=n.m.position;if(q.y<.12){q.y=.12;n.v.y*=-.4;n.v.x*=.7;n.v.z*=.7}
  for(const b of boxes)if(q.y<b.h&&q.x>b.x0&&q.x<b.x1&&q.z>b.z0&&q.z<b.z1){q.copy(o);n.v.x*=-.4;n.v.z*=-.4;n.v.y*=.5;break}if(n.t>1.6){popSmoke(q);S.remove(n.m);nades.splice(i,1)}}
 for(let i=smokes.length-1;i>=0;i--){const s=smokes[i];s.age+=dt;const e=Math.min(1,s.age);s.sp.forEach(x=>x.scale.setScalar(.5+(x.userData.tg-.5)*e));s.mt.opacity=.95*Math.min(1,(s.life-s.age)/3);if(s.age>s.life){S.remove(s.g);smokes.splice(i,1)}}
 for(let i=fx.length-1;i>=0;i--){const f=fx[i];f.t-=dt;if(f.t<=0){S.remove(f.o);fx.splice(i,1)}}for(const d of drops){d.t+=dt;d.m.rotation.y+=dt;d.m.position.y=d.y+.25+Math.sin(d.t*3)*.05}flashT=Math.max(0,flashT-dt*1.5)}

let buyOpen=false;
function toggleBuy(f){if(!running)return;if(buyOpen||f===false){buyOpen=false;$('buy').style.display='none';R.domElement.requestPointerLock();return}
 if(freeze<=0||freeze>100||dead||over){banner='Cumpărarea e posibilă doar la început de rundă';setTimeout(()=>{if(banner[0]==='C')banner=''},1800);return}
 buyOpen=true;fire=false;zoom=false;$('ov').style.display='none';document.exitPointerLock();$('buy').style.display='flex';renderBuy()}
function renderBuy(){$('bm').textContent='$'+P.money;const L=$('bl');L.innerHTML='';[['Pistoale',1,4],['SMG',5,6],['Pușți',7,9],['Lunetă',10,11]].forEach(([t,a,b])=>{const h=document.createElement('h3');h.textContent=t;L.appendChild(h);const r=document.createElement('div');r.className='row';for(let i=a;i<=b;i++){const w=WP[i],e=document.createElement('div'),own=P.prim===i||P.sec===i;e.className='o'+(own?' on':'');e.style.opacity=P.money>=w.p||own?1:.4;e.innerHTML=w.n+'<small>corp '+w.d+' · cap '+Math.min(100,Math.round(w.d*2.8))+'</small><small>'+(1/w.r).toFixed(1)+' foc/s · '+w.mag+' gloanțe</small><span class="by">'+(own?'ECHIPAT':'CUMPĂRĂ $'+w.p)+'</span>';e.onclick=()=>buy(i);r.appendChild(e)}L.appendChild(r)})}
function buy(i){const w=WP[i];if(P.money<w.p||freeze<=0||dead||P.prim===i||P.sec===i)return;P.money-=w.p;if(w.s===0)P.prim=i;else P.sec=i;P.am[i]=w.mag;P.rs[i]=w.res;selW(i);snd({d:.08,f:2000,v:.5});renderBuy()}
let drops=[];
function dropW(wi,p){if(wi==null||wi<0)return;const m=gun(wi);m.scale.multiplyScalar(1.3);m.rotation.z=Math.PI/2;const y=p.y||0;m.position.set(p.x,y+.25,p.z);const ring=new T.Mesh(new T.RingGeometry(.5,.62,24),new T.MeshBasicMaterial({color:0xf5a623,side:T.DoubleSide,transparent:true,opacity:.7}));ring.rotation.x=-Math.PI/2;ring.position.set(p.x,y+.04,p.z);S.add(m);S.add(ring);drops.push({w:wi,m,ring,x:p.x,z:p.z,y,t:0})}
function nearDrop(){let n=null,bd=2.2;for(const d of drops){const di=Math.hypot(d.x-P.pos.x,d.z-P.pos.z);if(di<bd){bd=di;n=d}}return n}
function pickup(){const b=nearDrop();if(!b||dead)return;const w=WP[b.w];if(w.s===0)P.prim=b.w;else P.sec=b.w;P.am[b.w]=w.mag;P.rs[b.w]=w.res;P.w=-1;selW(b.w);S.remove(b.m);S.remove(b.ring);drops=drops.filter(x=>x!==b);snd({d:.08,f:2500,v:.5})}
function dmgPop(n,hs){if(!ST.dmg)return;const e=document.createElement('div');e.className='dp';e.textContent=(hs?'HEADSHOT ':'')+'-'+Math.round(n);e.style.fontSize=Math.min(48,18+n/6)+'px';e.style.color=hs?'#ff5050':'#ffd24a';e.style.marginLeft=(20+Math.random()*30)+'px';e.style.marginTop=(-10+Math.random()*20)+'px';document.body.appendChild(e);requestAnimationFrame(()=>{e.style.transform='translateY(-70px)';e.style.opacity=0});setTimeout(()=>e.remove(),900)}
function renderSet(){const L=$('sl');L.innerHTML='';SETS.forEach(a=>{if(a.length===1){const h=document.createElement('h3');h.textContent=a[0];L.appendChild(h);return}const[k,t,mn,mx,sp]=a,l=document.createElement('label');l.className='s';const i=document.createElement('input');
 if(mn==='color'){i.type='color';i.value=ST[k];i.oninput=()=>{ST[k]=i.value;SAVE()};l.textContent=t;l.appendChild(i)}else{i.type='range';i.min=mn;i.max=mx;i.step=sp;i.value=ST[k];const b=document.createElement('b');b.textContent=ST[k];l.append(t+' ',b,i);i.oninput=()=>{ST[k]=+i.value;b.textContent=ST[k];SAVE();if(MX)MX.gain.value=1.3*ST.vol;sun.castShadow=!!ST.shd}}L.appendChild(l)})}
function renderInv(){$('co').textContent=WS.coins+' monede';$('oc2').style.opacity=WS.coins>=300?1:.4;const L=$('il');L.innerHTML='';WS.inv.forEach(it=>{const e=document.createElement('div'),on=WS.eq[it.w]===it.k,c='#'+SK[it.k][1].toString(16).padStart(6,0);e.className='o'+(on?' on':'');e.style.borderColor=c;e.innerHTML=WP[it.w].n+'<small style="color:'+c+'">'+SK[it.k][0]+(on?' · echipat':'')+'</small>';e.onclick=()=>{if(on)delete WS.eq[it.w];else WS.eq[it.w]=it.k;saveW();applySkins();renderInv()};L.appendChild(e)});if(!WS.inv.length)L.innerHTML='<span class="s">Gol — deschide o cutie.</span>'}
document.querySelectorAll('.bst').forEach(b=>b.onclick=()=>{renderSet();$('st').style.display='flex'});$('sx').onclick=()=>$('st').style.display='none';
document.querySelectorAll('.binv').forEach(b=>b.onclick=()=>{renderInv();$('inv').style.display='flex'});$('ix').onclick=()=>$('inv').style.display='none';$('bb').onclick=()=>toggleBuy();
$('oc2').onclick=()=>{if(WS.coins<300)return;WS.coins-=300;const r=Math.random(),ra=r<.05?2:r<.3?1:0,pool=[];SK.forEach((x,i)=>{if(i&&x[2]===ra)pool.push(i)});const k=pool[Math.random()*pool.length|0],w=Math.random()*WP.length|0;WS.inv.push({w,k});saveW();$('cr').innerHTML='Ai primit: <b style="color:#'+SK[k][1].toString(16).padStart(6,0)+'">'+WP[w].n+' | '+SK[k][0]+'</b> ('+['comun','rar','legendar'][ra]+')';renderInv()};
// ---- HUD ----
const rd=$('rad').getContext('2d');
function hud(){const m=Math.ceil(timeLeft);$('tm').textContent=Math.floor(m/60)+':'+String(m%60).padStart(2,'0');$('ct').textContent=s0;$('tt').textContent=s1;
 $('hp').innerHTML='<small style="font-size:16px;color:#ccc">♥ VIAȚĂ</small> '+Math.ceil(P.hp)+'<div style="width:200px;height:9px;background:#0008;border-radius:5px;margin-top:2px;border:1px solid #fff3"><div style="width:'+P.hp+'%;height:100%;border-radius:5px;background:'+(P.hp>50?'#4c4':P.hp>25?'#ec3':'#e33')+'"></div></div>';$('am').innerHTML=(P.rl>0?'<small>reîncărcare </small>':'')+P.am[P.w]+' <small>/ '+P.rs[P.w]+'</small>'+(P.smk?'<div style="font-size:14px;color:#ccc">☁ smoke ×'+P.smk+'</div>':'');
 $('wl').innerHTML=[P.prim,P.sec].map((i,n)=>i<0?'':(i===P.w?'<b>':'')+(n+1)+' '+WP[i].n+' · '+WP[i].d+' dmg'+(i===P.w?'</b>':'')).join('<br>')+'<br>B cumpără · Q schimbă';$('mo').textContent='$'+P.money;{const n=nearDrop();$('hn').textContent=n&&!dead?'E — ridică '+WP[n.w].n:''}$('fl').style.opacity=flashT;$('msg').textContent=banner||(freeze>0&&started?'Freeze time':'');
 const sn2=zoom&&WP[P.w].sn,g=ST.chg+Math.hypot(P.vx,P.vz)*1.2+P.burst*1.2+(P.og?0:8),ci=$('ch').children,L=sn2?0:ST.chs,t=ST.cht,h=t/2;$('ch').style.setProperty('--c',ST.chc);$('ch').style.opacity=sn2?0:ST.cho;
 ci[0].style.cssText=`left:${-h}px;top:${-g-L}px;width:${t}px;height:${L}px`;ci[1].style.cssText=`left:${-h}px;top:${g}px;width:${t}px;height:${L}px`;ci[2].style.cssText=`top:${-h}px;left:${-g-L}px;height:${t}px;width:${L}px`;ci[3].style.cssText=`top:${-h}px;left:${g}px;height:${t}px;width:${L}px`;ci[4].style.cssText=ST.chd?`left:${-h-.5}px;top:${-h-.5}px;width:${t+1}px;height:${t+1}px`:'display:none';
 rd.clearRect(0,0,150,150);rd.save();rd.beginPath();rd.arc(75,75,73,0,7);rd.clip();rd.fillStyle='rgba(20,22,28,.78)';rd.fillRect(0,0,150,150);
 const sc=1.7,cs=Math.cos(P.yaw),sn=Math.sin(P.yaw),tr=(x,z)=>{const rx=x-P.pos.x,rz=z-P.pos.z;return[75+(rx*cs-rz*sn)*sc,75+(rx*sn+rz*cs)*sc]};
 rd.fillStyle='rgba(190,175,150,.55)';for(const b of boxes){if(b.edge)continue;rd.beginPath();[[b.x0,b.z0],[b.x1,b.z0],[b.x1,b.z1],[b.x0,b.z1]].forEach(([x,z],i)=>{const[a,c]=tr(x,z);i?rd.lineTo(a,c):rd.moveTo(a,c)});rd.fill()}
 const dot=(p,c)=>{const[a,b]=tr(p.x,p.z);rd.fillStyle=c;rd.beginPath();rd.arc(a,b,4,0,7);rd.fill()};
 bots.forEach(b=>b.sees&&dot(b.g.position,'#f33'));Object.values(rem).forEach(c=>{if(c.g.visible&&(c.team===myTeam?1:c.sees))dot(c.g.position,c.team===myTeam?'#6ea8ff':'#f33')});
 rd.fillStyle='#fff';rd.beginPath();rd.moveTo(75,66);rd.lineTo(70,82);rd.lineTo(80,82);rd.fill();rd.restore()}
let last=performance.now();
function loop(now){requestAnimationFrame(loop);const dt=Math.min((now-last)/1000,.05);last=now;if(running){if(locked||buyOpen||online)update(dt);hud()}R.render(S,C)}

// ---- start ----
$('go').onclick=async()=>{ac();myName=($('nm').value||'Player').slice(0,12);$('nm2').value=myName;mapM=MAPS[mm];buildMap(mapM);need=MODES[ms][3];online=need>1;code=($('cd').value||'meci1').toLowerCase().replace(/[^a-z0-9]/g,'');
 $('menu').style.display='none';running=true;R.domElement.requestPointerLock();
 if(online){try{const r=window.claude&&await claude.use('room');if(r){room=await r.join('cs-'+code+'-'+MODES[ms][0]+'-'+mm);room.on('hit',m=>{if(m.data&&m.data.to===myId&&!m.sameTab)hurt(Math.min(999,+m.data.d||0),m.peer)});
   room.on('shot',m=>{const d=m.data;if(!m.isMe&&d)shotSnd(d.w|0,tv.set(d.x,0,d.z),.9)});room.on('kill',m=>{if(m.data&&m.data.x!==undefined)dropW(m.data.w|0,{x:m.data.x,y:m.data.y,z:m.data.z});if(m.data&&m.data.k===myId)P.money=Math.min(16000,P.money+300);if(!m.isMe&&m.data)feed(nameOf(m.data.k),nameOf(m.peer))});await room.presence({n:myName,tm:pref,a:0,r:0})}}catch(e){room=null}}
 else newRound()};
requestAnimationFrame(loop);
</script></body></html>

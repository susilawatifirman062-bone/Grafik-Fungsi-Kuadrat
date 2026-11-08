<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, viewport-fit=cover">
<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="theme-color" content="#0f2a43">
<title>Lab Maya Grafik Fungsi Kuadrat</title>
<style>
:root{--bg:#0f2a43;--card:#ffffff;--tx:#17233a;--mut:#56657d;--pri:#1565c0;--acc:#f57c00;--ok:#2e7d32;--bad:#c62828;--bd:#d5deea;--soft:#eef4fb;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#050d16;--card:#16202e;--tx:#e6edf7;--mut:#9fb0c8;--pri:#64a8ff;--acc:#ffb04d;--bd:#2b3a50;--soft:#1d2a3c;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#050d16;--card:#16202e;--tx:#e6edf7;--mut:#9fb0c8;--pri:#64a8ff;--acc:#ffb04d;--bd:#2b3a50;--soft:#1d2a3c;color-scheme:dark}
html,body{height:100%;margin:0;overscroll-behavior:none;-webkit-text-size-adjust:100%;touch-action:manipulation;-webkit-tap-highlight-color:transparent}
body{position:fixed;inset:0;background:var(--bg);display:flex;align-items:center;justify-content:center;font-family:system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;overflow:hidden}
#stage{position:fixed;left:50%;top:50%;transform:translate(-50%,-50%);width:100vw;height:56.25vw;background:var(--card);color:var(--tx);display:flex;flex-direction:column;overflow:hidden;font-size:16px}
header{display:flex;align-items:center;gap:.6em;padding:.5em .9em;background:var(--pri);color:#fff}
header h1{font-size:1.15em;margin:0;flex:1;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
header button{background:rgba(255,255,255,.18);color:#fff;border:1px solid rgba(255,255,255,.45)}
nav{display:flex;background:var(--soft);border-bottom:1px solid var(--bd)}
nav button{flex:1;border:0;background:none;padding:.65em .3em;font-size:.95em;font-weight:600;color:var(--mut);border-bottom:.2em solid transparent;cursor:pointer;border-radius:0}
nav button.on{color:var(--pri);border-color:var(--acc);background:var(--card)}
main{flex:1;min-height:0;position:relative}
section{position:absolute;inset:0;overflow:auto;padding:.9em 1.2em;display:none}
section.on{display:block}
button{font:inherit;cursor:pointer;border-radius:.45em;padding:.4em .9em;border:1px solid var(--pri);background:var(--pri);color:#fff;font-weight:600}
button.alt{background:var(--card);color:var(--pri)}
h2{margin:.1em 0 .4em;font-size:1.25em;color:var(--pri)}h3{margin:.8em 0 .3em;font-size:1.05em}
p,li{line-height:1.5;margin:.3em 0}
.grid{display:grid;grid-template-columns:1fr 1fr;gap:1em}
.box{background:var(--soft);border:1px solid var(--bd);border-radius:.6em;padding:.6em .9em}
.f{font-family:Georgia,"Times New Roman",serif;font-style:italic;color:var(--pri);font-weight:700}
table{border-collapse:collapse;width:100%;font-size:.92em}td,th{border:1px solid var(--bd);padding:.35em .5em;text-align:left}th{background:var(--soft)}
.sim{display:grid;grid-template-columns:1.5fr 1fr;gap:1em;height:100%}
.cv{position:relative;min-height:0}canvas{width:100%;height:100%;display:block;background:#fff;border:1px solid var(--bd);border-radius:.5em}
.ctl{overflow:auto}.ctl label{display:block;margin:.35em 0;font-weight:600}.ctl input[type=range]{width:100%}
.out div{margin:.2em 0}.out b{color:var(--pri)}
.q{border:1px solid var(--bd);border-radius:.6em;padding:.6em .9em;margin:.6em 0}
.q label{display:block;padding:.25em .4em;border-radius:.4em;cursor:pointer}
.q label.ok{background:#c8e6c9;color:#14361a}.q label.no{background:#ffcdd2;color:#4a1010}
.ex{margin-top:.3em;color:var(--mut);font-size:.92em}
input[type=text],input[type=password]{font:inherit;padding:.4em .6em;border:1px solid var(--bd);border-radius:.4em;background:var(--card);color:var(--tx)}
#splash{--splash:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 160 90'%3E%3Crect width='160' height='90' fill='%230f2a43'/%3E%3Cpath d='M5 -10Q80 170 155 -10M30 -10Q80 120 130 -10' fill='none' stroke='%2364a8ff' stroke-opacity='.35' stroke-width='1.2'/%3E%3C/svg%3E");position:absolute;inset:0;z-index:20;display:flex;align-items:center;justify-content:center;text-align:center;color:#fff;background:linear-gradient(135deg,rgba(13,71,161,.88),rgba(106,27,154,.8) 55%,rgba(230,81,0,.78)),var(--splash);background-size:cover;background-position:center;transition:opacity .5s}
#splash.off{opacity:0;pointer-events:none}
.sp-in{max-width:60%}
.sp-badge{display:inline-block;background:var(--acc);color:#111;font-weight:700;padding:.2em .8em;border-radius:2em;font-size:.9em}
.sp-in h1{font-size:2.6em;margin:.4em 0;line-height:1.15}
.sp-in p{opacity:.9;font-size:1.05em}
.sp-bar{height:.7em;background:rgba(255,255,255,.25);border-radius:1em;overflow:hidden;margin:1.2em auto .4em;width:70%}
.sp-bar i{display:block;height:100%;width:0;background:linear-gradient(90deg,#ffca28,#ff6f00);transition:width .15s}
#spTxt{font-size:.9em;margin-bottom:.9em}
#bMulai{background:linear-gradient(90deg,#ffca28,#ff6f00);border-color:#ffca28;color:#111;font-size:1.3em;padding:.5em 2em}
#bMulai:disabled{opacity:.45;cursor:not-allowed}
.sp-ph{position:absolute;right:.8em;bottom:.6em;font-size:.75em;opacity:.7}
.sp-school{font-size:1.3em;font-weight:800;letter-spacing:.08em;text-transform:uppercase;margin-bottom:.5em}
.sp-dev{position:absolute;left:1em;bottom:.7em;text-align:left;line-height:1.25;font-family:Pacifico,"Brush Script MT","Segoe Script",cursive;font-size:1.6em;font-weight:400;text-shadow:0 .08em .25em rgba(0,0,0,.45)}
.sp-dev small{display:block;font-family:system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;font-size:.5em;letter-spacing:.12em;text-transform:uppercase;opacity:.85}
.net{font-size:.8em;background:rgba(255,255,255,.2);padding:.2em .6em;border-radius:1em;white-space:nowrap}
button{min-height:2.2em}
</style>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap">
</head>
<body>
<div id="stage">
<div id="splash"><div class="sp-in"><div class="sp-school">SMA Negeri 4 Kota Ternate</div><div class="sp-badge">SMA/MA · Kelas X · Fase E</div><h1>Lab Maya<br>Grafik Fungsi Kuadrat</h1><p>Menggambar parabola, menentukan titik puncak, sumbu simetri, dan titik potong, serta menyelesaikan masalah kontekstual.</p><div class="sp-bar"><i id="spBar"></i></div><div id="spTxt">Memuat… 0%</div><button id="bMulai" disabled>Mulai</button></div><div class="sp-dev"><small>Pengembang</small>Susilawati Firman, S.Pd</div><div class="sp-ph">Gambar latar (placeholder)</div></div>
<header><h1>Lab Maya Grafik Fungsi Kuadrat · Kelas X · Fase E</h1>
<span id="net" class="net"></span><button id="bSnd" class="alt" title="Suara">Suara: aktif</button>
<button id="bRst">Reset</button><button id="bFs">Layar penuh</button></header>
<nav id="nav"></nav>
<main>
<section id="t0">
<div class="grid"><div>
<h2>Teori Fungsi Kuadrat</h2>
<p><b>Fungsi kuadrat</b> berbentuk <span class="f">f(x) = ax² + bx + c</span> dengan a, b, c bilangan real dan a ≠ 0. Grafiknya berupa kurva <b>parabola</b>.</p>
<ul><li>a &gt; 0: parabola terbuka ke atas (memiliki nilai minimum).</li><li>a &lt; 0: parabola terbuka ke bawah (memiliki nilai maksimum).</li><li>Semakin besar |a|, parabola semakin sempit.</li></ul>
<h3>Unsur-unsur grafik</h3>
<div class="box"><p>Sumbu simetri: <span class="f">x = −b / 2a</span></p><p>Titik puncak: <span class="f">(−b/2a , −D/4a)</span>, dengan D = b² − 4ac</p><p>Titik potong sumbu y: <span class="f">(0, c)</span></p><p>Titik potong sumbu x: akar dari ax² + bx + c = 0, yaitu <span class="f">x = (−b ± √D) / 2a</span></p></div>
</div><div>
<h3>Diskriminan (D = b² − 4ac)</h3>
<table><tr><th>Nilai D</th><th>Akar</th><th>Grafik terhadap sumbu x</th></tr>
<tr><td>D &gt; 0</td><td>Dua akar real berbeda</td><td>Memotong di dua titik</td></tr>
<tr><td>D = 0</td><td>Satu akar real kembar</td><td>Menyinggung di puncak</td></tr>
<tr><td>D &lt; 0</td><td>Dua akar imajiner (kompleks sekawan)</td><td>Tidak memotong sumbu x</td></tr></table>
<h3>Akar imajiner</h3>
<p>Karena i = √−1, maka √D = √|D| · i untuk D &lt; 0. Contoh: x² − 2x + 5 = 0 memiliki D = −16 sehingga x = 1 ± 2i.</p>
<h3>Bentuk lain</h3>
<p>Bentuk puncak: <span class="f">f(x) = a(x − p)² + q</span> dengan puncak (p, q). Bentuk faktor: <span class="f">f(x) = a(x − x₁)(x − x₂)</span>.</p>
<h3>Masalah kontekstual</h3>
<p>Nilai maksimum/minimum (tinggi lemparan bola, luas terbesar, laba tertinggi) terjadi di titik puncak.</p>
</div></div></section>

<section id="t1">
<h2>Prosedur Menggambar Grafik</h2>
<div class="grid"><div>
<ol><li><b>Tentukan a, b, c</b> dan arah bukaan (a &gt; 0 ke atas, a &lt; 0 ke bawah).</li>
<li><b>Hitung D = b² − 4ac</b> untuk mengetahui jenis akar.</li>
<li><b>Sumbu simetri</b>: x = −b/2a.</li>
<li><b>Titik puncak</b>: substitusi x tersebut ke f(x), atau gunakan y = −D/4a.</li>
<li><b>Titik potong sumbu y</b>: (0, c).</li>
<li><b>Titik potong sumbu x</b>: selesaikan ax² + bx + c = 0 (jika D ≥ 0).</li>
<li><b>Titik bantu</b>: ambil beberapa nilai x di kiri dan kanan sumbu simetri.</li>
<li><b>Gambar</b>: hubungkan titik-titik dengan kurva mulus yang simetris.</li></ol>
<p>Tips: cek jawaban dengan menggeser a, b, c pada tab <b>Simulasi</b>.</p></div>
<div class="box"><h3>Contoh: f(x) = x² − 4x + 3</h3>
<p>1. a = 1, b = −4, c = 3 → terbuka ke atas.</p><p>2. D = 16 − 12 = 4 &gt; 0 → dua titik potong sumbu x.</p><p>3. Sumbu simetri: x = 4/2 = 2.</p><p>4. Puncak: f(2) = 4 − 8 + 3 = −1 → (2, −1).</p><p>5. Titik potong y: (0, 3).</p><p>6. Titik potong x: (x−1)(x−3) = 0 → (1, 0) dan (3, 0).</p>
<p><button id="bEx">Coba di Simulasi</button></p></div></div></section>

<section id="t2">
<div class="sim"><div class="cv"><canvas id="cv"></canvas></div>
<div class="ctl"><h2>Simulasi: f(x) = ax² + bx + c</h2>
<label>a = <span id="va"></span><input type="range" id="a" min="-5" max="5" step="0.1"></label>
<label>b = <span id="vb"></span><input type="range" id="b" min="-10" max="10" step="0.5"></label>
<label>c = <span id="vc"></span><input type="range" id="c" min="-10" max="10" step="0.5"></label>
<label><input type="checkbox" id="kP" checked> Puncak</label>
<label><input type="checkbox" id="kS" checked> Sumbu simetri</label>
<label><input type="checkbox" id="kX" checked> Titik potong</label>
<div class="box out" id="out"></div></div></div></section>

<section id="t3"></section>

<section id="t4"></section>
</main></div>

<script>
var $=function(i){return document.getElementById(i)};
var TABS=["Teori","Prosedur","Simulasi","Soal Individu","Hasil Kerja"],cur=0,snd=true,AC=null;
function beep(f){if(!snd)return;try{AC=AC||new (window.AudioContext||window.webkitAudioContext)();if(AC.state==="suspended")AC.resume();var o=AC.createOscillator(),g=AC.createGain();o.frequency.value=f||660;o.type="triangle";g.gain.value=.08;g.gain.exponentialRampToValueAtTime(.0001,AC.currentTime+.12);o.connect(g);g.connect(AC.destination);o.start();o.stop(AC.currentTime+.12)}catch(e){}}
document.addEventListener("click",function(e){if(e.target.closest("button,label,input[type=radio]"))beep()});
function fit(){var s=$("stage"),vv=window.visualViewport,W=vv?vv.width:innerWidth,H=vv?vv.height:innerHeight,rot=H>W*1.1&&W<900,aw=rot?H:W,ah=rot?W:H,sw=Math.min(aw,ah*16/9),sh=sw*9/16;s.style.width=sw+"px";s.style.height=sh+"px";s.style.transform="translate(-50%,-50%)"+(rot?" rotate(90deg)":"");s.style.fontSize=Math.max(7,sw/78)+"px";draw()}
window.addEventListener("resize",fit);window.addEventListener("orientationchange",function(){setTimeout(fit,250)});if(window.visualViewport)visualViewport.addEventListener("resize",fit);
function enterFs(){var d=document.documentElement,f=d.requestFullscreen||d.webkitRequestFullscreen;if(f)try{var r=f.call(d);if(r&&r.catch)r.catch(function(){})}catch(e){}}
function fsChg(){var on=document.fullscreenElement||document.webkitFullscreenElement;$("bFs").textContent=on?"Keluar layar penuh":"Layar penuh";setTimeout(fit,150)}
document.addEventListener("fullscreenchange",fsChg);document.addEventListener("webkitfullscreenchange",fsChg);
$("nav").innerHTML=TABS.map(function(t,i){return '<button data-i="'+i+'">'+(i+1)+'. '+t+'</button>'}).join("");
$("nav").onclick=function(e){var b=e.target.closest("button");if(b)go(+b.dataset.i)};
function go(i){cur=i;for(var k=0;k<5;k++){$("t"+k).classList.toggle("on",k==i);$("nav").children[k].classList.toggle("on",k==i)}if(i==2)setTimeout(draw,30);if(i==3&&!$("t3").innerHTML)quizStart();if(i==4)lockView()}
$("bSnd").onclick=function(){snd=!snd;this.textContent="Suara: "+(snd?"aktif":"mati")};
$("bFs").onclick=function(){var d=document.documentElement;if(!(d.requestFullscreen||d.webkitRequestFullscreen)){alert("Peramban ini (mis. iPhone) tidak mendukung layar penuh otomatis. Tampilan sudah menyesuaikan layar; putar HP ke mode landscape, atau gunakan Bagikan > Tambah ke Layar Utama.");return}var fe=document.fullscreenElement||document.webkitFullscreenElement;try{if(fe)(document.exitFullscreen||document.webkitExitFullscreen).call(document);else enterFs()}catch(e){}};
$("bRst").onclick=function(){if(cur==2)setABC(1,-4,3);else if(cur==3)quizStart();else if(cur==4)lockView();else go(cur)};

/* ---------- Simulasi ---------- */
function fmt(n){var r=Math.round(n*100)/100;return String(r).replace(".",",")}
function setABC(a,b,c){$("a").value=a;$("b").value=b;$("c").value=c;draw()}
$("bEx").onclick=function(){setABC(1,-4,3);go(2)};
["a","b","c","kP","kS","kX"].forEach(function(i){$(i).oninput=draw;$(i).onchange=draw});
function draw(){
 var a=+$("a").value,b=+$("b").value,c=+$("c").value;
 $("va").textContent=fmt(a);$("vb").textContent=fmt(b);$("vc").textContent=fmt(c);
 var cv=$("cv"),w=cv.clientWidth,h=cv.clientHeight;if(!w||!h)return;
 var d=window.devicePixelRatio||1;cv.width=w*d;cv.height=h*d;var x=cv.getContext("2d");x.setTransform(d,0,0,d,0,0);
 x.clearRect(0,0,w,h);var R=12,sx=w/(2*R),sy=h/(2*R),ox=w/2,oy=h/2;
 function X(v){return ox+v*sx}function Y(v){return oy-v*sy}
 x.font="11px sans-serif";x.lineWidth=1;
 for(var i=-R;i<=R;i++){x.strokeStyle=i==0?"#222":"#dde6f0";x.lineWidth=i==0?1.6:1;x.beginPath();x.moveTo(X(i),0);x.lineTo(X(i),h);x.stroke();x.beginPath();x.moveTo(0,Y(i));x.lineTo(w,Y(i));x.stroke();
  if(i&&i%2==0){x.fillStyle="#445";x.fillText(i,X(i)+2,oy+12);x.fillText(i,ox+3,Y(i)-2)}}
 var out=$("out");
 if(Math.abs(a)<0.05){out.innerHTML="<b>a = 0</b> bukan fungsi kuadrat (menjadi garis lurus). Ubah nilai a.";x.strokeStyle="#c62828";x.lineWidth=2;x.beginPath();x.moveTo(X(-R),Y(-b*R+c));x.lineTo(X(R),Y(b*R+c));x.stroke();return}
 var D=Math.round((b*b-4*a*c)*1e6)/1e6,xp=-b/(2*a),yp=-D/(4*a);
 x.strokeStyle="#1565c0";x.lineWidth=3;x.beginPath();
 for(var px=0;px<=w;px+=2){var v=(px-ox)/sx,y=a*v*v+b*v+c;px?x.lineTo(px,Y(y)):x.moveTo(px,Y(y))}x.stroke();
 function dot(vx,vy,col,t){x.fillStyle=col;x.beginPath();x.arc(X(vx),Y(vy),5,0,7);x.fill();x.fillStyle="#222";x.fillText(t,X(vx)+7,Y(vy)-7)}
 if($("kS").checked){x.setLineDash([6,4]);x.strokeStyle="#f57c00";x.lineWidth=2;x.beginPath();x.moveTo(X(xp),0);x.lineTo(X(xp),h);x.stroke();x.setLineDash([])}
 if($("kP").checked)dot(xp,yp,"#f57c00","("+fmt(xp)+", "+fmt(yp)+")");
 var rt="";
 if(D>0){var r1=(-b-Math.sqrt(D))/(2*a),r2=(-b+Math.sqrt(D))/(2*a);rt="x₁ = <b>"+fmt(Math.min(r1,r2))+"</b>, x₂ = <b>"+fmt(Math.max(r1,r2))+"</b>";if($("kX").checked){dot(r1,0,"#2e7d32",fmt(r1));dot(r2,0,"#2e7d32",fmt(r2))}}
 else if(D==0){rt="x₁ = x₂ = <b>"+fmt(xp)+"</b>";if($("kX").checked)dot(xp,0,"#2e7d32",fmt(xp))}
 else{rt="x = <b>"+fmt(xp)+" ± "+fmt(Math.sqrt(-D)/(2*Math.abs(a)))+"i</b> (imajiner)"}
 if($("kX").checked)dot(0,c,"#8e24aa","(0, "+fmt(c)+")");
 out.innerHTML="<div>Fungsi: <b>y = "+fmt(a)+"x² "+(b<0?"− ":"+ ")+fmt(Math.abs(b))+"x "+(c<0?"− ":"+ ")+fmt(Math.abs(c))+"</b></div><div>Arah: <b>"+(a>0?"terbuka ke atas (minimum)":"terbuka ke bawah (maksimum)")+"</b></div><div>D = b² − 4ac = <b>"+fmt(D)+"</b> → "+(D>0?"dua akar real":D==0?"akar kembar":"akar imajiner, tidak memotong sumbu x")+"</div><div>Sumbu simetri: x = <b>"+fmt(xp)+"</b></div><div>Titik puncak: <b>("+fmt(xp)+", "+fmt(yp)+")</b></div><div>Titik potong y: <b>(0, "+fmt(c)+")</b></div><div>Akar: "+rt+"</div>";
}

/* ---------- Bank soal (jawaban benar ditulis pertama, urutan opsi diacak saat tampil) ---------- */
var BANK=[
["Titik puncak grafik y = x² − 4x + 3 adalah …","(2, −1)","(−2, 1)","(2, 1)","(4, 3)","x = −b/2a = 2 dan y = 4 − 8 + 3 = −1."],
["Sumbu simetri grafik y = x² − 6x + 5 adalah …","x = 3","x = −3","x = 6","x = 5","x = −b/2a = 6/2 = 3."],
["Titik potong grafik y = 2x² − 3x + 7 dengan sumbu y adalah …","(0, 7)","(7, 0)","(0, −3)","(0, 2)","Substitusi x = 0 sehingga y = c = 7."],
["Titik potong grafik y = x² − 5x + 6 dengan sumbu x adalah …","(2, 0) dan (3, 0)","(−2, 0) dan (−3, 0)","(1, 0) dan (6, 0)","(0, 2) dan (0, 3)","x² − 5x + 6 = (x − 2)(x − 3) = 0."],
["Grafik y = −x² + 2x + 3 …","terbuka ke bawah karena a &lt; 0","terbuka ke atas karena a &gt; 0","terbuka ke bawah karena c &gt; 0","terbuka ke kanan","Arah bukaan ditentukan tanda a. Di sini a = −1."],
["Diskriminan dari x² − 4x + 5 = 0 adalah …","−4","4","12","36","D = (−4)² − 4(1)(5) = 16 − 20 = −4."],
["Akar-akar dari x² + 4 = 0 adalah …","x = ±2i","x = ±2","x = 4","x = −4","x² = −4 sehingga x = ±√(−4) = ±2i."],
["Nilai minimum fungsi y = x² − 2x + 3 adalah …","2","3","1","−2","Puncak di x = 1, y = 1 − 2 + 3 = 2."],
["Nilai maksimum fungsi y = −2x² + 8x − 3 adalah …","5","−3","8","3","x = 2 lalu y = −8 + 16 − 3 = 5."],
["Grafik y = x² − 2x − 3 memotong sumbu x di …","(−1, 0) dan (3, 0)","(1, 0) dan (−3, 0)","(−1, 0) dan (−3, 0)","(1, 0) dan (3, 0)","(x + 1)(x − 3) = 0."],
["Jika D &gt; 0 maka grafik fungsi kuadrat …","memotong sumbu x di dua titik berbeda","menyinggung sumbu x","tidak memotong sumbu x","memotong sumbu x di satu titik saja","D &gt; 0 berarti dua akar real berbeda."],
["Jika D = 0 maka grafik fungsi kuadrat …","menyinggung sumbu x","memotong sumbu x di dua titik","tidak memotong sumbu x","berada di atas sumbu x tanpa menyentuhnya","Akar kembar, puncak berada tepat pada sumbu x."],
["Titik puncak grafik y = −x² + 6x − 5 adalah …","(3, 4)","(3, −4)","(−3, 4)","(6, −5)","x = 3 dan y = −9 + 18 − 5 = 4."],
["Titik puncak grafik y = 2(x − 1)² + 3 adalah …","(1, 3)","(−1, 3)","(1, −3)","(2, 3)","Bentuk puncak a(x − p)² + q memiliki puncak (p, q)."],
["Fungsi kuadrat dengan puncak (1, −4) dan melalui (0, −3) adalah …","y = x² − 2x − 3","y = x² + 2x − 3","y = x² − 2x + 3","y = −x² + 2x − 3","y = a(x − 1)² − 4; x = 0, y = −3 memberi a = 1."],
["Akar-akar dari x² − x − 6 = 0 adalah …","3 dan −2","−3 dan 2","6 dan −1","2 dan 3","(x − 3)(x + 2) = 0."],
["Akar-akar dari x² − 2x + 5 = 0 adalah …","1 ± 2i","2 ± i","−1 ± 2i","1 ± 4i","D = −16 sehingga x = (2 ± 4i)/2 = 1 ± 2i."],
["Sumbu simetri grafik y = −x² + 4x + 1 adalah …","x = 2","x = −2","x = 4","x = −4","x = −4/(2·(−1)) = 2."],
["Titik potong sumbu y dari y = (x − 2)(x + 3) adalah …","(0, −6)","(0, 6)","(0, −1)","(0, 5)","f(0) = (−2)(3) = −6."],
["Agar grafik y = x² − 6x + c menyinggung sumbu x, nilai c adalah …","9","6","3","36","D = 36 − 4c = 0 sehingga c = 9."],
["Persamaan x² + kx + 4 = 0 memiliki akar imajiner jika …","−4 &lt; k &lt; 4","k &lt; −4 atau k &gt; 4","k &gt; 4","k = ±4","D = k² − 16 &lt; 0 sehingga −4 &lt; k &lt; 4."],
["Tinggi bola h(t) = −5t² + 20t (meter). Tinggi maksimum bola adalah … meter.","20","40","10","15","t = 2, h = −20 + 40 = 20."],
["Pada h(t) = −5t² + 20t, bola kembali ke tanah pada t = … detik.","4","2","5","20","−5t(t − 4) = 0 sehingga t = 4."],
["Petani memiliki pagar 40 m untuk kandang persegi panjang. Luas terbesar yang mungkin adalah … m².","100","400","200","80","L = x(20 − x), maksimum saat x = 10 sehingga L = 100."],
["Laba (dalam ribu rupiah) dari x unit barang adalah P(x) = −2x² + 40x − 100. Laba maksimum dicapai saat x = … unit.","10","20","100","40","x = −40/(2·(−2)) = 10."],
["Lengkung jembatan y = −x² + 16 (meter). Lebar dasar jembatan (y = 0) adalah … m.","8","16","4","32","x² = 16 sehingga x = ±4, lebar = 8 m."],
["Dua bilangan berjumlah 12. Hasil kali terbesar keduanya adalah …","36","35","32","24","x(12 − x) maksimum saat x = 6, hasilnya 36."],
["Titik potong sumbu x grafik y = x² − 4 adalah …","(−2, 0) dan (2, 0)","(0, −4) dan (0, 4)","(4, 0) dan (−4, 0)","(0, 2) dan (0, −2)","x² = 4 sehingga x = ±2."],
["Grafik y = x² + 2x + 5 …","tidak memotong sumbu x; akarnya imajiner","memotong sumbu x di dua titik","menyinggung sumbu x","memotong sumbu x di (−5, 0)","D = 4 − 20 = −16 &lt; 0."],
["Grafik y = x² digeser 2 satuan ke kanan dan 3 satuan ke bawah menjadi …","y = (x − 2)² − 3","y = (x + 2)² − 3","y = (x − 2)² + 3","y = (x + 3)² − 2","Geser kanan p: x → x − p; geser bawah q: kurang q."]
];
var Z=[],nama="";
function shuf(a){a=a.slice();for(var i=a.length-1;i>0;i--){var j=Math.floor(Math.random()*(i+1)),t=a[i];a[i]=a[j];a[j]=t}return a}
function quizStart(){nama="";Z=[];$("t3").innerHTML='<h2>Soal Individu</h2><p>Kerjakan 5 soal acak dari 30 soal pilihan ganda (menggambar grafik, titik puncak, sumbu simetri, titik potong, dan masalah kontekstual).</p><p><input type="text" id="nm" placeholder="Nama murid" maxlength="40"> <input type="text" id="kl" placeholder="Kelas (mis. X-1)" maxlength="10" style="width:9em"> <button id="mulai">Mulai</button></p>';$("mulai").onclick=quizRun}
function quizRun(){nama=$("nm").value.trim();if(!nama){$("nm").focus();return}var kl=$("kl").value.trim();
 Z=shuf(BANK.map(function(_,i){return i})).slice(0,5).map(function(i){var q=BANK[i];return{q:q[0],o:shuf([1,2,3,4].map(function(k){return{t:q[k],ok:k==1}})),e:q[5],kl:kl}});
 var h='<h2>Soal Individu</h2><p id="nmh"></p>';
 Z.forEach(function(z,i){h+='<div class="q"><b>'+(i+1)+'. '+z.q+'</b>'+z.o.map(function(o,j){return '<label><input type="radio" name="q'+i+'" value="'+j+'"> '+String.fromCharCode(65+j)+'. '+o.t+'</label>'}).join("")+'<div class="ex" id="ex'+i+'"></div></div>'});
 h+='<p><button id="kirim">Kirim jawaban</button> <span id="sk"></span></p>';$("t3").innerHTML=h;$("nmh").textContent="Nama: "+nama;$("kirim").onclick=quizEnd}
function quizEnd(){var s=0,miss=0;Z.forEach(function(z,i){if(!document.querySelector('input[name=q'+i+']:checked'))miss++});
 if(miss&&!confirm("Ada "+miss+" soal belum dijawab. Tetap kirim?"))return;
 Z.forEach(function(z,i){var c=document.querySelector('input[name=q'+i+']:checked'),ls=document.querySelectorAll('input[name=q'+i+']');
  ls.forEach(function(r,j){r.disabled=true;if(z.o[j].ok)r.parentNode.classList.add("ok");else if(r.checked)r.parentNode.classList.add("no")});
  if(c&&z.o[+c.value].ok)s++;$("ex"+i).innerHTML="Pembahasan: "+z.e});
 var nilai=s*20;$("sk").innerHTML="<b>Skor: "+s+" / 5 (nilai "+nilai+")</b>";$("kirim").disabled=true;beep(nilai>=60?880:300);
 saveRecord({id:"m"+Date.now().toString(36)+Math.random().toString(36).slice(2,8),nama:nama,kelas:Z[0].kl,nilai:nilai,benar:s,ts:Date.now()});$("sk").innerHTML+=" <small>(hasil dikirim ke guru"+(navigator.onLine===false?" saat online kembali":"")+")</small>"}

/* ---------- Penyimpanan online/offline ---------- */
var URL_WEBAPP="";/* opsional: isi URL web app (.../exec) jika file ini dibuka sebagai file lokal */
var GAS=(typeof google!=="undefined"&&google.script&&google.script.run)?google.script.run:null,QK="lmk_antrian",MEM=[],flushing=false;
function qGet(){try{return JSON.parse(localStorage.getItem(QK)||"[]")}catch(e){return MEM}}
function qSet(a){MEM=a;try{localStorage.setItem(QK,JSON.stringify(a))}catch(e){}}
function netUi(){var n=qGet().length;$("net").textContent=(navigator.onLine===false?"Offline":"Online")+(n?" · "+n+" antrian":"")}
function call(fn,args,ok,err){if(!GAS){err("Tidak terhubung ke server. Buka lewat tautan web app Google Apps Script.");return}var r=GAS.withSuccessHandler(ok).withFailureHandler(function(e){err(e&&e.message?e.message:String(e))});r[fn].apply(r,args)}
function kirim(rec,ok,err){if(GAS)call("simpanHasil",[rec],ok,err);else if(URL_WEBAPP)fetch(URL_WEBAPP,{method:"POST",mode:"no-cors",headers:{"Content-Type":"text/plain;charset=utf-8"},body:JSON.stringify(rec)}).then(function(){ok()},function(e){err(String(e))});else err("no-server")}
function saveRecord(r){var q=qGet();q.push(r);qSet(q);netUi();flush()}
function flush(){var q=qGet();if(flushing||!q.length||navigator.onLine===false||(!GAS&&!URL_WEBAPP)){netUi();return}flushing=true;kirim(q[0],function(){var c=qGet();c.shift();qSet(c);flushing=false;netUi();flush()},function(){flushing=false;netUi()})}
window.addEventListener("online",function(){netUi();flush()});window.addEventListener("offline",netUi);setInterval(flush,20000);

/* ---------- Hasil Kerja (guru / pengembang): password diperiksa di server ---------- */
function lockView(){$("t4").innerHTML='<h2>Hasil Kerja Murid</h2><p>Halaman ini hanya untuk guru dan pengembang. Data diambil dari server (perlu internet) sehingga dapat dibuka dari perangkat mana saja.</p><p><input type="password" id="pw" placeholder="Password"> <button id="buka">Buka</button> <span id="pe" style="color:var(--bad)"></span></p>';
 function cek(){var pw=$("pw").value;$("pe").textContent="Memeriksa\u2026";call("getHasil",[pw],function(res){if(!res||!res.ok){$("pe").textContent="Password salah.";beep(250);return}showRes(res.rows,pw)},function(m){$("pe").textContent=m})}
 $("buka").onclick=cek;$("pw").onkeydown=function(e){if(e.key==="Enter")cek()}}
function showRes(rows,pw){var sum=0;rows.forEach(function(r){sum+=+r.nilai||0});
 var h='<h2>Hasil Kerja Murid</h2><p>'+rows.length+' data'+(rows.length?', rata-rata nilai '+Math.round(sum/rows.length*10)/10:'')+'. <button id="mm" class="alt">Muat ulang</button> <button id="hps" class="alt">Hapus semua</button> <button id="kunci" class="alt">Kunci</button> <span id="pe2"></span></p><table><tr><th>No</th><th>Nama</th><th>Kelas</th><th>Nilai</th><th>Benar</th><th>Waktu</th></tr>';
 rows.forEach(function(r,i){h+='<tr><td>'+(i+1)+'</td><td></td><td></td><td></td><td></td><td></td></tr>'});h+='</table>';$("t4").innerHTML=h;
 var tr=$("t4").querySelectorAll("tr");rows.forEach(function(r,i){var td=tr[i+1].children;td[1].textContent=r.nama;td[2].textContent=r.kelas||"-";td[3].textContent=r.nilai;td[4].textContent=r.benar+"/5";td[5].textContent=r.waktu});
 $("mm").onclick=function(){$("pe2").textContent="Memuat\u2026";call("getHasil",[pw],function(x){if(x&&x.ok)showRes(x.rows,pw)},function(m){$("pe2").textContent=m})};
 $("hps").onclick=function(){if(confirm("Hapus semua hasil di server?"))call("hapusSemua",[pw],function(){showRes([],pw)},function(m){$("pe2").textContent=m})};
 $("kunci").onclick=lockView}
netUi();flush();

var spP=0,spT=setInterval(function(){spP=Math.min(100,spP+Math.random()*9+3);$("spBar").style.width=spP+"%";$("spTxt").textContent=spP>=100?"Siap!":"Memuat… "+Math.floor(spP)+"%";if(spP>=100){clearInterval(spT);$("bMulai").disabled=false}},150);
$("bMulai").onclick=function(){beep(880);setTimeout(function(){beep(1175)},110);enterFs();$("splash").classList.add("off");setTimeout(function(){$("splash").style.display="none";fit()},500)};
setABC(1,-4,3);go(0);fit();
</script>
</body>
</html>

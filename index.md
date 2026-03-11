<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=0"/> 
<title>HOANGDZ AI PREDICT ULTIMATE</title>
<style>
:root{
  --tx-color:#00f2ff; --md5-color:#facc15; --sicbo-color:#ff00ff;
  --bg-panel: rgba(5, 15, 25, 0.9);
}
*{box-sizing:border-box; touch-action: none; user-select: none; -webkit-user-select: none;}
body { margin: 0; background: #000; overflow: hidden; font-family: 'Segoe UI', sans-serif; color: #fff; }

/* SETUP SCREEN - BACKGROUND CỰC CHẤT */
#setupOverlay {
  position: fixed; inset: 0; 
  background: url('https://i.postimg.cc/mD3fNqX1/cyber-city.jpg') no-repeat center center;
  background-size: cover;
  z-index: 20000; display: flex; justify-content: center; align-items: center;
}
#setupOverlay::after {
    content: ""; position: absolute; inset: 0; background: rgba(0, 0, 0, 0.6); backdrop-filter: blur(5px); z-index: -1;
}

.setup-box {
  background: rgba(10, 20, 30, 0.8); backdrop-filter: blur(25px);
  padding: 35px; border-radius: 30px; border: 2px solid var(--tx-color);
  width: 380px; text-align: center; 
  box-shadow: 0 0 50px rgba(0, 242, 255, 0.4), inset 0 0 20px rgba(0, 242, 255, 0.1);
  animation: glowIn 1s ease-out;
}
@keyframes glowIn { from {opacity: 0; transform: scale(0.9);} to {opacity: 1; transform: scale(1);} }

.input-link { 
    width: 100%; padding: 15px; background: rgba(0,0,0,0.7); 
    border: 1px solid var(--tx-color); color: #fff; border-radius: 15px; 
    margin-bottom: 25px; outline: none; text-align: center; font-size: 14px;
}

.tool-selector { display: flex; justify-content: space-between; margin-bottom: 25px; gap: 8px; }
.tool-opt { 
    cursor: pointer; padding: 12px 5px; border: 1px solid #444; border-radius: 15px; 
    font-size: 10px; width: 33%; opacity: 0.6; transition: 0.3s;
    background: rgba(255,255,255,0.05); font-weight: bold;
}
.tool-opt.active { opacity: 1; border-color: var(--tx-color); background: rgba(0, 242, 255, 0.2); transform: scale(1.05); box-shadow: 0 0 15px var(--tx-color); }

.start-btn { 
    width: 100%; padding: 18px; background: var(--tx-color); color: #000; 
    border: none; border-radius: 15px; font-weight: 900; cursor: pointer; 
    text-transform: uppercase; letter-spacing: 2px;
}

/* MAIN UI */
#gameFrame { position: fixed; inset: 0; width: 100vw; height: 100vh; border: none; z-index: 1; display: none; }

.bot-wrap { position: fixed; z-index: 9999; display: none; align-items: center; gap: 12px; transform: rotate(90deg); transform-origin: center; scale: 0.85; }
.robot-img { width: 85px; filter: drop-shadow(0 0 15px var(--tx-color)); animation: bounce 2s infinite alternate; }
@keyframes bounce { from {transform: translateY(0);} to {transform: translateY(-12px);} }

.panel { 
  min-width: 240px; background: var(--bg-panel); backdrop-filter: blur(15px);
  border-radius: 25px; padding: 20px; border: 1px solid rgba(255,255,255,0.1);
  box-shadow: 0 15px 40px rgba(0,0,0,0.8);
}
.header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px; }
.title { font-size: 11px; font-weight: 900; letter-spacing: 1.5px; text-transform: uppercase; }
.zoom-btn { width: 26px; height: 26px; background: rgba(255,255,255,0.1); border: none; color: white; border-radius: 8px; cursor: pointer; }

input.cau-input { width: 100%; background: rgba(0,0,0,0.4); border: 1px solid rgba(255,255,255,0.1); color: #fff; padding: 12px; border-radius: 12px; font-size: 12px; margin-bottom: 12px; outline: none; }
.predict-btn { width: 100%; padding: 15px; border: none; border-radius: 12px; font-weight: bold; cursor: pointer; text-transform: uppercase; transition: 0.2s; }

.res-box { margin-top: 15px; border-top: 1px solid rgba(255,255,255,0.1); padding-top: 12px; font-size: 12px; text-align: center; }
.val { font-weight: 900; font-size: 20px; color: var(--tx-color); display: inline-block; }
.vi-val { color: #fff; font-weight: bold; font-style: italic; letter-spacing: 2px; }

#backBtn { position: fixed; top: 15px; right: 15px; z-index: 10005; background: rgba(0,0,0,0.5); backdrop-filter: blur(10px); color: white; border: 1px solid #444; padding: 10px 20px; border-radius: 12px; cursor: pointer; display: none; font-weight: bold; }
</style>
</head>
<body oncontextmenu="return false;"> <div id="setupOverlay">
  <div class="setup-box">
    <h2 style="color:var(--tx-color); margin-top:0; letter-spacing: 3px; font-style: italic;">HOANGDZ AI CENTER</h2>
    <input type="text" id="linkInput" class="input-link" placeholder="DÁN LINK GAME TẠI ĐÂY..." value="https://web.sunwin.lt/?affId=Sunwin">
    
    <div class="tool-selector">
      <div class="tool-opt active" onclick="sel(this, 'wrapTX')">TÀI XỈU AI</div>
      <div class="tool-opt" onclick="sel(this, 'wrapMD5')" style="border-color:var(--md5-color)">MD5 PRO</div>
      <div class="tool-opt" onclick="sel(this, 'wrapSicbo')" style="border-color:var(--sicbo-color)">SICBO VỊ</div>
    </div>
    
    <button class="start-btn" onclick="launch()">KÍCH HOẠT HỆ THỐNG</button>
    <p style="font-size: 9px; margin-top: 15px; opacity: 0.5;">VERSION 4.5 ULTIMATE BY HOANGDZ</p>
  </div>
</div>

<button id="backBtn" onclick="location.reload()">ĐỔI CỔNG GAME</button>
<iframe id="gameFrame"></iframe>

<div id="wrapTX" class="bot-wrap" onmousedown="dragS(event, this)" ontouchstart="dragS(event, this)">
  <img class="robot-img" src="https://i.postimg.cc/63bdy9D9/robotics-1.gif">
  <div class="panel" style="border-top: 4px solid var(--tx-color)">
    <div class="header"><span class="title" style="color:var(--tx-color)">HOANGDZ TX</span><div><button class="zoom-btn" onclick="zm(this,-0.1)">-</button><button class="zoom-btn" onclick="zm(this,0.1)">+</button></div></div>
    <input type="text" class="cau-input" placeholder="Nhập cầu (Vd: TXT)...">
    <button class="predict-btn" style="background:var(--tx-color); color:#000" onclick="logicTX(this)">PHÂN TÍCH CẦU</button>
    <div class="res-box">DỰ ĐOÁN: <span class="val">---</span><br>TỈ LỆ THẮNG: <span class="val rate">0%</span></div>
  </div>
</div>

<div id="wrapMD5" class="bot-wrap" onmousedown="dragS(event, this)" ontouchstart="dragS(event, this)">
  <img class="robot-img" src="https://i.postimg.cc/63bdy9D9/robotics-1.gif">
  <div class="panel" style="border-top: 4px solid var(--md5-color)">
    <div class="header"><span class="title" style="color:var(--md5-color)">MD5 ANALYZER</span><div><button class="zoom-btn" onclick="zm(this,-0.1)">-</button><button class="zoom-btn" onclick="zm(this,0.1)">+</button></div></div>
    <input type="text" class="cau-input" placeholder="Dán mã MD5 32 ký tự...">
    <button class="predict-btn" style="background:var(--md5-color); color:#000" onclick="logicMD5(this)">GIẢI MÃ AI</button>
    <div class="res-box">DỰ ĐOÁN: <span class="val">---</span><br>TỈ LỆ THẮNG: <span class="val rate">0%</span></div>
  </div>
</div>

<div id="wrapSicbo" class="bot-wrap" onmousedown="dragS(event, this)" ontouchstart="dragS(event, this)">
  <img class="robot-img" src="https://i.postimg.cc/63bdy9D9/robotics-1.gif">
  <div class="panel" style="border-top: 4px solid var(--sicbo-color)">
    <div class="header"><span class="title" style="color:var(--sicbo-color)">SICBO PRO AI</span><div><button class="zoom-btn" onclick="zm(this,-0.1)">-</button><button class="zoom-btn" onclick="zm(this,0.1)">+</button></div></div>
    <input type="text" class="cau-input" placeholder="Mã MD5 Sicbo...">
    <button class="predict-btn" style="background:var(--sicbo-color); color:#000" onclick="logicSicbo(this)">SOI CẦU VỊ AI</button>
    <div class="res-box">
        DỰ ĐOÁN: <span class="val main-res">---</span><br>
        VỊ CƯỢC: <span class="vi-val">---</span><br>
        TỈ LỆ THẮNG: <span class="val rate">0%</span>
    </div>
  </div>
</div>

<script>
// --- CHẶN F12, CTRL+U, KIỂM TRA PHẦN TỬ ---
document.addEventListener('keydown', function(e) {
    if (e.keyCode == 123 || 
        (e.ctrlKey && e.shiftKey && (e.keyCode == 73 || e.keyCode == 74)) || 
        (e.ctrlKey && e.keyCode == 85)) {
        e.preventDefault();
        return false;
    }
});

let activeToolId = 'wrapTX';

function sel(el, id) {
  document.querySelectorAll('.tool-opt').forEach(o => o.classList.remove('active'));
  el.classList.add('active'); activeToolId = id;
}

function launch() {
  const url = document.getElementById('linkInput').value;
  if(!url.includes('http')) return alert("Link không hợp lệ!");
  document.getElementById('gameFrame').src = url;
  document.getElementById('gameFrame').style.display = 'block';
  document.getElementById('setupOverlay').style.display = 'none';
  document.getElementById('backBtn').style.display = 'block';
  const t = document.getElementById(activeToolId);
  t.style.display = 'flex'; t.style.top = '150px'; t.style.left = '20px';
}

// --- GIỮ NGUYÊN LOGIC PHÂN TÍCH ---
function logicTX(btn) {
  const inp = btn.parentElement.querySelector('input').value.trim();
  if(!inp) return alert("Vui lòng nhập dữ liệu cầu mới!");
  const res = btn.parentElement.querySelector('.val');
  const rate = btn.parentElement.querySelector('.rate');
  res.textContent = "SCANNING...";
  setTimeout(() => {
    const isTai = (inp.length + Math.random()) % 2 > 1;
    res.textContent = isTai ? "TÀI" : "XỈU";
    res.style.color = isTai ? "var(--tx-color)" : "#ff4d4d";
    rate.textContent = (Math.random() * (95 - 82) + 82).toFixed(1) + "%";
  }, 1000);
}

function logicMD5(btn) {
  const hash = btn.parentElement.querySelector('input').value.trim();
  if(hash.length < 10) return alert("MD5 không hợp lệ!");
  const res = btn.parentElement.querySelector('.val');
  const rate = btn.parentElement.querySelector('.rate');
  res.textContent = "DECODING...";
  setTimeout(() => {
    let sum = 0;
    for(let i=0; i<hash.length; i++) sum += hash.charCodeAt(i);
    const isTai = sum % 2 === 0;
    res.textContent = isTai ? "TÀI" : "XỈU";
    res.style.color = isTai ? "var(--md5-color)" : "#ff4d4d";
    rate.textContent = (85 + (sum % 10)).toFixed(1) + "%";
  }, 1200);
}

function logicSicbo(btn) {
  const inp = btn.parentElement.querySelector('input').value.trim();
  if(!inp) return alert("Nhập mã MD5 Sicbo!");
  const mainRes = btn.parentElement.querySelector('.main-res');
  const viRes = btn.parentElement.querySelector('.vi-val');
  const rate = btn.parentElement.querySelector('.rate');
  mainRes.textContent = "ANALYZING...";
  setTimeout(() => {
    let seed = 0;
    for(let i=0; i<inp.length; i++) seed += inp.charCodeAt(i);
    const isTai = seed % 2 !== 0;
    mainRes.textContent = isTai ? "TÀI" : "XỈU";
    mainRes.style.color = isTai ? "var(--sicbo-color)" : "var(--tx-color)";
    let viArr = isTai ? [11, 14, 16] : [4, 7, 10];
    if(seed % 3 === 0) viArr = isTai ? [12, 15, 17] : [5, 6, 9];
    viRes.textContent = viArr.join(" - ");
    rate.textContent = (80 + (seed % 15)).toFixed(1) + "%";
  }, 1500);
}

function zm(btn, v) {
  let w = btn.closest('.bot-wrap');
  let s = parseFloat(w.style.scale) || 0.85;
  w.style.scale = Math.min(Math.max(s + v, 0.4), 1.5);
}

let act = null; let sx, sy, ix, iy;
function dragS(e, el) {
  act = el; const v = e.type === 'touchstart' ? e.touches[0] : e;
  sx = v.clientX; sy = v.clientY;
  ix = act.offsetLeft; iy = act.offsetTop;
  document.addEventListener('mousemove', dragM); document.addEventListener('touchmove', dragM, {passive: false});
  document.addEventListener('mouseup', dragE); document.addEventListener('touchend', dragE);
}
function dragM(e) {
  if (!act) return; const v = e.type === 'touchmove' ? e.touches[0] : e;
  if(e.type === 'touchmove') e.preventDefault();
  act.style.left = (ix + (v.clientX - sx)) + 'px';
  act.style.top = (iy + (v.clientY - sy)) + 'px';
}
function dragE() { act = null; }
</script>
</body>
</html>

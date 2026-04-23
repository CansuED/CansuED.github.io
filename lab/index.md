---
layout: lab
title: 
permalink: /lab/
---

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<div class="lab-page">
  <div id="lab-hero">
    <canvas id="spiral-canvas"></canvas>
    <div id="canvas-vignette"></div>
    <div id="lab-text">
      <p class="lab-eyebrow">Research Lab</p>
      <h1 class="lab-hero-title">
        <span class="lab-title-plain">Welcome to the</span>
        <span class="lab-title-highlight">D^4 Sustainable Futures</span>
        <span class="lab-title-plain">Lab</span>
      </h1>
      <p class="lab-hero-subtitle">
        Harnessing <strong class="lab-subtitle-strong">Digital, Data, Design, and Development</strong>
        to imagine and build sustainable futures
      </p>
    </div>
  </div>
</div>

<script>
document.addEventListener('DOMContentLoaded', function () {
  'use strict';

  var seed = 1234;
  function rng(){ seed=(seed*9301+49297)%233280; return seed/233280; }

  var canvas = document.getElementById('spiral-canvas');
  if (!canvas) return;
  var ctx = canvas.getContext('2d');
  var dpr = window.devicePixelRatio || 1;
  var W = 0, H = 0;

  function resize(){
    W = window.innerWidth;
    H = window.innerHeight;
    canvas.style.width  = W + 'px';
    canvas.style.height = H + 'px';
    canvas.width  = W * dpr;
    canvas.height = H * dpr;
    ctx.setTransform(dpr,0,0,dpr,0,0);
  }
  resize();
  window.addEventListener('resize', resize);

  var CAM_Z = -400, CAM_T = 3400, ZOOM = 100, YOF = 28;
  var CHG   = 0.32, MS = 15000, NS = 4000;

  function clamp(v,a,b){return Math.min(Math.max(v,a),b);}
  function mapv(v,a,b,c,d){return c+(d-c)*((v-a)/(b-a));}
  function lerp(a,b,t){return a*(1-t)+b*t;}
  function eg(p,g){return p<.5?.5*Math.pow(2*p,g):1-.5*Math.pow(2*(1-p),g);}
  function ee(x){
    if(x<=0)return 0; if(x>=1)return 1;
    return Math.pow(2,-8*x)*Math.sin((x*8-.75)*(2*Math.PI)/4.5)+1;
  }
  function spiral(p){
    p=clamp(1.2*p,0,1); p=eg(p,1.8);
    var th=2*Math.PI*6*Math.sqrt(p), r=170*Math.sqrt(p);
    return{x:r*Math.cos(th), y:r*Math.sin(th)+YOF};
  }
  function dark(){return document.documentElement.getAttribute('data-theme')==='dark';}
  function themeBg(){
    if(!dark()) return '#ffffff';
    var val = getComputedStyle(document.documentElement).getPropertyValue('--bg-color').trim();
    return val || '#09090e';
  }

  var stars=[];
  for(var i=0;i<NS;i++){
    var a=rng()*Math.PI*2, d=30*rng()+15;
    var sl=(1-Math.pow(1-rng(),3))/1.3;
    var zr=lerp(.5*CAM_Z, CAM_T+CAM_Z, rng());
    stars.push({
      a:a, d:d, rd:rng()>.5?1:-1,
      er:1.2+rng()*.8, fs:.7+rng()*.6,
      dx:d*Math.cos(a), dy:d*Math.sin(a),
      sl:sl, z:lerp(zr,CAM_T/2,.3*sl),
      sw:Math.pow(rng(),2)
    });
  }

  function drawStar(s,p,t,col){
    var sp=spiral(s.sl), q=p-s.sl;
    if(q<=0)return;
    var dp=clamp(4*q,0,1);
    var eased;
    if(dp<.3)      eased=lerp(dp,dp*dp,dp/.3);
    else if(dp<.7) eased=lerp(dp*dp,ee(dp),(dp-.3)/.4);
    else           eased=ee(dp);

    var sx,sy;
    if(dp<.3){
      var f=eased/.3;
      sx=lerp(sp.x,sp.x+s.dx*.3,f); sy=lerp(sp.y,sp.y+s.dy*.3,f);
    } else if(dp<.7){
      var mp=(dp-.3)/.4, cs=Math.sin(mp*Math.PI)*s.rd*1.5;
      var bx=sp.x+s.dx*.3, by=sp.y+s.dy*.3;
      sx=lerp(bx,sp.x+s.dx*.7,mp)+(-s.dy*.4*cs)*mp;
      sy=lerp(by,sp.y+s.dy*.7,mp)+(s.dx*.4*cs)*mp;
    } else {
      var fp=(dp-.7)/.3;
      var sa=s.a+1.2*s.rd*fp*Math.PI;
      sx=lerp(sp.x+s.dx*.7, sp.x+s.d*s.er*1.5*Math.cos(sa), fp);
      sy=lerp(sp.y+s.dy*.7, sp.y+s.d*s.er*1.5*Math.sin(sa), fp);
    }

    var t2=clamp(mapv(t,CHG,1,0,1),0,1);
    var cz=CAM_Z+eg(Math.pow(t2,1.2),1.8)*CAM_T;
    if(s.z<=cz)return;
    var dep=s.z-cz;
    var px=ZOOM*sx/dep, py=ZOOM*sy/dep;
    var sm=dp<.6?1+dp*.2:lerp(1.2,s.fs,(dp-.6)/.4);
    var sw=400*(8.5*s.sw*sm)/dep;
    ctx.fillStyle=col;
    ctx.beginPath(); ctx.arc(px,py,Math.max(sw/2,.3),0,Math.PI*2); ctx.fill();
  }

  var t0=null;
  function frame(now){
    requestAnimationFrame(frame);
    if(!t0)t0=now;
    var t  = ((now-t0)%MS)/MS;
    var t1 = clamp(mapv(t,0,CHG+.25,0,1),0,1);
    var t2 = clamp(mapv(t,CHG,1,0,1),0,1);
    var bg  = themeBg();
    var dot = dark() ? 'rgba(100,201,230,0.45)' : 'rgba(28,46,64,0.35)';
    ctx.fillStyle=bg; ctx.fillRect(0,0,W,H);
    ctx.save();
    ctx.translate(W/2, H/2);
    ctx.rotate(-Math.PI*eg(t2,2.7));
    for(var j=0;j<stars.length;j++) drawStar(stars[j],t1,t,dot);
    ctx.restore();
  }
  requestAnimationFrame(frame);
  setTimeout(function(){ canvas.classList.add('loaded'); }, 150);
});
</script>

<script>
(function () {
  if (window.__themeTransitionLab) return;
  window.__themeTransitionLab = true;

  function isThemeToggle(el) {
    if (!el) return false;
    var sig = (el.className || '') + (el.title || '') +
              (el.getAttribute('aria-label') || '') + (el.innerHTML || '');
    return /dark|light|theme|color.?scheme|sun|moon|☀|🌙/i.test(sig);
  }

  var fallbackTimer = null;
  function cssTransitionFallback() {
    clearTimeout(fallbackTimer);
    document.documentElement.classList.add('is-theme-transitioning');
    fallbackTimer = setTimeout(function () {
      document.documentElement.classList.remove('is-theme-transitioning');
    }, 950);
  }

  var _replaying = false;
  document.addEventListener('click', function (e) {
    if (_replaying) return;
    var btn = e.target;
    while (btn && btn !== document.documentElement) {
      if ((btn.tagName === 'BUTTON' || btn.getAttribute('role') === 'button') && isThemeToggle(btn)) break;
      btn = btn.parentElement;
    }
    if (!btn || btn === document.documentElement) return;
    var r = btn.getBoundingClientRect();
    document.documentElement.style.setProperty('--vt-x', (r.left + r.width / 2).toFixed(1) + 'px');
    document.documentElement.style.setProperty('--vt-y', (r.top + r.height / 2).toFixed(1) + 'px');
    if (typeof document.startViewTransition === 'function') {
      e.stopImmediatePropagation();
      document.startViewTransition(function () {
        _replaying = true;
        btn.dispatchEvent(new MouseEvent('click', { bubbles: true, cancelable: true }));
        _replaying = false;
      });
    } else {
      cssTransitionFallback();
    }
  }, true);

  document.addEventListener('keydown', function (e) {
    if (e.key !== ' ' && e.key !== 'Enter') return;
    if (document.activeElement && isThemeToggle(document.activeElement)) cssTransitionFallback();
  });
}());
</script>
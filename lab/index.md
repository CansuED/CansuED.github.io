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
(function () {
  'use strict';

  var canvas = document.getElementById('spiral-canvas');
  if (!canvas) return;
  var ctx = canvas.getContext('2d');
  var dpr = window.devicePixelRatio || 1;
  var W = 0, H = 0;

  function resize() {
    W = window.innerWidth;
    H = window.innerHeight;
    canvas.style.width  = W + 'px';
    canvas.style.height = H + 'px';
    canvas.width  = W * dpr;
    canvas.height = H * dpr;
    ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
    /* Reset all prev-positions on resize so no stale streak lines appear */
    for (var i = 0; i < pts.length; i++) { pts[i].psx = null; pts[i].psy = null; }
  }

  /* ── Seeded RNG ──────────────────────────────────────── */
  var seed = 42;
  function rng() { seed = (seed * 9301 + 49297) % 233280; return seed / 233280; }

  /* ── Particle field ──────────────────────────────────── */
  var N        = 520;
  var NEAR     = 40;
  var FAR      = 1400;
  var SPEED    = 180;   /* units/second — feel free to tweak */
  var SPREAD_X = 580;
  var SPREAD_Y = 400;

  var pts = [];
  for (var i = 0; i < N; i++) {
    pts.push({
      x:   (rng() - 0.5) * 2 * SPREAD_X,
      y:   (rng() - 0.5) * 2 * SPREAD_Y,
      z:   NEAR + rng() * (FAR - NEAR),
      psx: null,   /* previous screen x — used to draw streak */
      psy: null,
      r:   0.7 + rng() * 2.3,
      b:   0.35 + rng() * 0.65   /* brightness factor */
    });
  }

  /* ── Theme helpers ───────────────────────────────────── */
  function dark() {
    var el = document.documentElement;
    return el.getAttribute('data-theme') === 'dark' ||
           el.classList.contains('dark') ||
           document.body.classList.contains('dark-theme');
  }
  function themeBg() {
    if (!dark()) return '#ffffff';
    var v = getComputedStyle(document.documentElement).getPropertyValue('--bg-color').trim();
    return v || '#0d0d14';
  }

  /* ── Animation loop ──────────────────────────────────── */
  var t0 = null, last = null;

  function frame(now) {
    requestAnimationFrame(frame);
    if (!t0) { t0 = now; last = now; }
    var dt      = Math.min((now - last) / 1000, 0.05);   /* seconds, capped */
    last        = now;
    var elapsed = (now - t0) / 1000;

    var W2 = W / 2, H2 = H / 2;
    var dk = dark();

    /* Brand teal: light mode (58,154,184) | dark mode (100,201,230) */
    var dotR = dk ? 100 : 58;
    var dotG = dk ? 201 : 154;
    var dotB = dk ? 230 : 184;
    var dotCol = 'rgb(' + dotR + ',' + dotG + ',' + dotB + ')';

    /* Soft trail — overdraw background at low opacity each frame */
    ctx.fillStyle  = themeBg();
    ctx.globalAlpha = 0.28;
    ctx.fillRect(0, 0, W, H);
    ctx.globalAlpha = 1;

    /* Gentle sinusoidal camera sway — feels alive but not nauseating */
    var camX = Math.sin(elapsed * 0.17) * 24;
    var camY = Math.cos(elapsed * 0.12) * 16;

    for (var i = 0; i < pts.length; i++) {
      var p = pts[i];

      /* Advance toward camera */
      p.z -= SPEED * dt;

      /* Wrap: reset particle to far plane individually — no global jump */
      if (p.z < NEAR) {
        p.x   = (rng() - 0.5) * 2 * SPREAD_X;
        p.y   = (rng() - 0.5) * 2 * SPREAD_Y;
        p.z   = FAR;
        p.psx = null;
        p.psy = null;
        continue;
      }

      /* Perspective projection */
      var sc = 400 / p.z;
      var sx = W2 + (p.x + camX) * sc;
      var sy = H2 + (p.y + camY) * sc;

      /* Cull off-screen */
      if (sx < -10 || sx > W + 10 || sy < -10 || sy > H + 10) {
        p.psx = null; p.psy = null; continue;
      }

      /* Depth-based opacity: fade in from far, fade out when very close */
      var farFade  = Math.min(1, (FAR - p.z) / (FAR * 0.22));
      var nearFade = Math.min(1, (p.z - NEAR) / (NEAR * 3.5));
      var alpha    = p.b * farFade * nearFade * 0.58;
      if (alpha <= 0.002) { p.psx = null; p.psy = null; continue; }

      ctx.globalAlpha = Math.min(alpha, 0.55);
      ctx.fillStyle   = dotCol;
      ctx.strokeStyle = dotCol;

      /* Draw streak from previous position — creates natural motion trail */
      if (p.psx !== null) {
        var r = Math.max(0.25, p.r * sc * 0.55);
        ctx.lineWidth = Math.max(0.4, r * 1.7);
        ctx.lineCap   = 'round';
        ctx.beginPath();
        ctx.moveTo(p.psx, p.psy);
        ctx.lineTo(sx, sy);
        ctx.stroke();
      }

      /* Draw dot at current tip */
      ctx.beginPath();
      ctx.arc(sx, sy, Math.max(0.3, p.r * sc * 0.55), 0, Math.PI * 2);
      ctx.fill();

      p.psx = sx;
      p.psy = sy;
    }

    ctx.globalAlpha = 1;
  }

  resize();
  window.addEventListener('resize', resize);
  requestAnimationFrame(frame);
  setTimeout(function () { canvas.classList.add('loaded'); }, 150);
}());
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
    document.documentElement.style.setProperty('--vt-x', (r.left + r.width  / 2).toFixed(1) + 'px');
    document.documentElement.style.setProperty('--vt-y', (r.top  + r.height / 2).toFixed(1) + 'px');
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
---
layout: single
permalink: /
title: ""
author_profile: false
classes: wide
---

<!-- Outfit: clean, geometric, modern sans-serif -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;700&display=swap" rel="stylesheet">

<canvas id="dotted-canvas" aria-hidden="true"></canvas>
<div class="hero-glow" aria-hidden="true"></div>

<div class="homepage-content">

  <div class="profile-ring">
    <img src="/images/Cansu.jpeg" alt="Cansu Ekmekcioglu" class="profile-image">
  </div>

  <h1 class="hero-name">
    <span class="name-first">Cansu</span>
    <span class="name-last">Ekmekcioglu</span>
  </h1>

  <p class="hero-title">Assistant Professor of Information Systems</p>
  <p class="hero-institution">DeGroote School of Business &middot; McMaster University</p>

  <div class="social-links">
    <a href="mailto:ekmekcic@mcmaster.ca" class="social-link" aria-label="Email">
      <i class="fas fa-envelope"></i>
    </a>
    <a href="https://twitter.com/Cansu_ED" target="_blank" rel="noopener" class="social-link" aria-label="Twitter">
      <i class="fab fa-twitter"></i>
    </a>
    <a href="https://www.linkedin.com/in/cansu-ekmekcioglu/" target="_blank" rel="noopener" class="social-link" aria-label="LinkedIn">
      <i class="fab fa-linkedin"></i>
    </a>
    <a href="https://github.com/CansuED" target="_blank" rel="noopener" class="social-link" aria-label="GitHub">
      <i class="fab fa-github"></i>
    </a>
    <a href="https://scholar.google.ca/citations?user=piapLkEAAAAJ&hl=en" target="_blank" rel="noopener" class="social-link" aria-label="Google Scholar">
      <i class="fas fa-graduation-cap"></i>
    </a>
  </div>

</div>

<!-- ============================================================
     DOT-WAVE ANIMATION
     ============================================================ -->
<script>
(function () {
  'use strict';

  var canvas = document.getElementById('dotted-canvas');
  if (!canvas) return;
  var ctx = canvas.getContext('2d');

  var SEPARATION = 150;
  var AMOUNTX    = 40;
  var AMOUNTY    = 60;
  var CAM_Y      = 355;
  var CAM_Z      = 1220;
  var FOV_DEG    = 60;
  var count      = 0;

  function resize() {
    canvas.width  = window.innerWidth;
    canvas.height = window.innerHeight;
  }

  function isDark() {
    var el   = document.documentElement;
    var body = document.body;
    return (
      el.classList.contains('dark')            ||
      el.getAttribute('data-theme') === 'dark' ||
      body.classList.contains('dark-theme')    ||
      body.getAttribute('data-theme') === 'dark'
    );
  }

  function draw() {
    var W = canvas.width;
    var H = canvas.height;
    ctx.clearRect(0, 0, W, H);

    var dark = isDark();
    // Brand teal in light mode; desaturated teal in dark mode
    var dotR = dark ? 82  : 58;
    var dotG = dark ? 160 : 154;
    var dotB = dark ? 190 : 184;

    var fovFactor = H / (2 * Math.tan((FOV_DEG * Math.PI / 180) / 2));

    for (var ix = 0; ix < AMOUNTX; ix++) {
      for (var iy = 0; iy < AMOUNTY; iy++) {
        var x3d = ix * SEPARATION - (AMOUNTX * SEPARATION) / 2;
        var z3d = iy * SEPARATION - (AMOUNTY * SEPARATION) / 2;
        var y3d = Math.sin((ix + count) * 0.3) * 50 + Math.sin((iy + count) * 0.5) * 50;

        var depth = CAM_Z - z3d;
        if (depth < 1) continue;

        var scale   = fovFactor / depth;
        var sx      = W / 2 + x3d * scale;
        var sy      = H / 2 - (y3d - CAM_Y) * scale;

        if (sx < -20 || sx > W + 20 || sy < -20 || sy > H + 20) continue;

        var radius  = Math.max(0.4, 4 * scale);
        var opacity = Math.min(0.22, scale * 58);

        ctx.fillStyle = 'rgba(' + dotR + ',' + dotG + ',' + dotB + ',' + opacity.toFixed(3) + ')';
        ctx.beginPath();
        ctx.arc(sx, sy, radius, 0, 6.2832);
        ctx.fill();
      }
    }

    count += 0.04;
    requestAnimationFrame(draw);
  }

  resize();
  draw();
  window.addEventListener('resize', resize);
}());
</script>

<!-- ============================================================
     PREMIUM THEME TRANSITION
     ─────────────────────────────────────────────────────────────
     Strategy
     ────────
     1. Intercept every click on the theme-toggle button (capture
        phase, so we run before Minimal Mistakes' own handler).
     2. If the browser supports the View Transitions API, wrap
        the theme change in startViewTransition() so the SCSS
        @keyframes vt-radial-in plays: a circle expands from the
        button's exact centre, revealing the new theme underneath.
     3. On browsers without View Transitions (Firefox, older
        Safari) we fall back to the CSS class
        .is-theme-transitioning, which gives a smooth 0.45 s
        crossfade of colours instead.
     4. Reduced-motion users always get an instant swap — the CSS
        strips the transition when prefers-reduced-motion: reduce.
     ============================================================ -->
<script>
(function () {
  'use strict';

  // ── Helpers ──────────────────────────────────────────────────

  // Returns true if we are currently in dark mode.
  function isDark() {
    var el = document.documentElement;
    return (
      el.classList.contains('dark')            ||
      el.getAttribute('data-theme') === 'dark' ||
      document.body.classList.contains('dark-theme') ||
      document.body.getAttribute('data-theme') === 'dark'
    );
  }

  // Returns true if the element looks like the theme toggle button.
  function isThemeToggle(el) {
    if (!el) return false;
    var sig = (el.className || '') +
              (el.title     || '') +
              (el.getAttribute('aria-label') || '') +
              (el.innerHTML  || '');
    return /dark|light|theme|color.?scheme|sun|moon|☀|🌙/i.test(sig);
  }

  // Find the toggle button (best-effort; tries common Minimal Mistakes selectors).
  function findToggleBtn() {
    var selectors = [
      '.theme__toggler',
      '[data-theme-toggle]',
      'button[aria-label*="theme" i]',
      'button[title*="theme" i]',
      'button[aria-label*="dark" i]',
      'button[aria-label*="light" i]',
      'button[title*="dark" i]',
      'button[title*="light" i]'
    ];
    for (var i = 0; i < selectors.length; i++) {
      var btn = document.querySelector(selectors[i]);
      if (btn) return btn;
    }
    // Generic fallback: any button whose markup hints at theming
    var buttons = document.querySelectorAll('button, [role="button"]');
    for (var j = 0; j < buttons.length; j++) {
      if (isThemeToggle(buttons[j])) return buttons[j];
    }
    return null;
  }

  // ── CSS fallback ──────────────────────────────────────────────
  // Adds the transition class for 500 ms so SCSS kicks in.
  var fallbackTimer = null;
  function cssTransitionFallback() {
    clearTimeout(fallbackTimer);
    document.documentElement.classList.add('is-theme-transitioning');
    fallbackTimer = setTimeout(function () {
      document.documentElement.classList.remove('is-theme-transitioning');
    }, 950);
  }

  // ── View Transitions interception ─────────────────────────────
  // We use a flag to distinguish the synthetic re-dispatch from
  // the original user click, preventing infinite recursion.
  var _replaying = false;

  document.addEventListener('click', function (e) {
    // Skip our own re-dispatched event
    if (_replaying) return;

    // Walk up the DOM to find the actual button element
    var btn = e.target;
    while (btn && btn !== document.documentElement) {
      if (
        (btn.tagName === 'BUTTON' || btn.getAttribute('role') === 'button') &&
        isThemeToggle(btn)
      ) break;
      btn = btn.parentElement;
    }
    if (!btn || btn === document.documentElement) return;

    // Store the click origin as CSS custom properties so the SCSS
    // @keyframes can anchor the circle to the exact button centre.
    var r  = btn.getBoundingClientRect();
    var cx = (r.left + r.width  / 2).toFixed(1) + 'px';
    var cy = (r.top  + r.height / 2).toFixed(1) + 'px';
    document.documentElement.style.setProperty('--vt-x', cx);
    document.documentElement.style.setProperty('--vt-y', cy);

    if (typeof document.startViewTransition === 'function') {
      // View Transitions path — swallow the original click,
      // then re-fire it inside the transition callback.
      e.stopImmediatePropagation();
      document.startViewTransition(function () {
        _replaying = true;
        btn.dispatchEvent(new MouseEvent('click', { bubbles: true, cancelable: true }));
        _replaying = false;
      });
    } else {
      // CSS fallback path — just add the transition class; MM's
      // own handler fires normally and the crossfade plays.
      cssTransitionFallback();
    }

  }, true /* capture phase — runs before MM's own listeners */);

  // ── Keyboard support ─────────────────────────────────────────
  // Space / Enter on the toggle should also get the transition.
  document.addEventListener('keydown', function (e) {
    if (e.key !== ' ' && e.key !== 'Enter') return;
    var btn = document.activeElement;
    if (btn && isThemeToggle(btn)) {
      cssTransitionFallback();
    }
  });

}());
</script>
---
layout: single
permalink: /
title: ""
author_profile: false
classes: wide
---

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;700&display=swap" rel="stylesheet">

<div id="dot-wave" aria-hidden="true"></div>
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

<script>
(function() {
  var COLS = 18;
  var ROWS = 10;
  var SPEED = 2200;

  function build() {
    var container = document.getElementById('dot-wave');
    if (!container) { setTimeout(build, 100); return; }
    container.innerHTML = '';
    var wW = window.innerWidth;
    var wH = window.innerHeight;
    var spacingX = wW / (COLS - 1);
    var spacingY = wH / (ROWS - 1);
    for (var row = 0; row < ROWS; row++) {
      for (var col = 0; col < COLS; col++) {
        var dot = document.createElement('div');
        dot.className = 'dw-dot';
        var x = col * spacingX;
        var y = row * spacingY;
        var phaseDelay = ((col * 0.3 + row * 0.5) / (COLS * 0.3 + ROWS * 0.5)) * SPEED;
        var depth = 0.4 + (row / (ROWS - 1)) * 0.6;
        var size = Math.max(1.5, 4 * depth);
        var opacity = Math.min(0.22, 0.04 + depth * 0.18);
        dot.style.cssText = 'position:absolute;border-radius:50%;left:' + x.toFixed(1) + 'px;top:' + y.toFixed(1) + 'px;width:' + size.toFixed(1) + 'px;height:' + size.toFixed(1) + 'px;opacity:' + opacity.toFixed(3) + ';animation:dw-bob ' + SPEED + 'ms ease-in-out ' + phaseDelay.toFixed(0) + 'ms infinite alternate;background:rgb(58,154,184);transform:translateY(0)';
        container.appendChild(dot);
      }
    }
  }

  var style = document.createElement('style');
  style.textContent = '#dot-wave{position:fixed;inset:0;pointer-events:none;z-index:0;overflow:hidden;}@keyframes dw-bob{0%{transform:translateY(0)}100%{transform:translateY(-38px)}}html[data-theme=dark] #dot-wave .dw-dot,body.dark-theme #dot-wave .dw-dot{background:rgb(82,160,190)!important}';
  document.head.appendChild(style);

  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', build);
  } else {
    build();
  }

  var resizeTimer;
  window.addEventListener('resize', function() {
    clearTimeout(resizeTimer);
    resizeTimer = setTimeout(build, 150);
  });
}());
</script>

<script>
(function () {
  function isThemeToggle(el) {
    if (!el) return false;
    var sig = (el.className || '') + (el.title || '') + (el.getAttribute('aria-label') || '') + (el.innerHTML || '');
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
    if (isThemeToggle(document.activeElement)) cssTransitionFallback();
  });
}());
</script>
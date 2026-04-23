---
layout: single
title: "Contact"
permalink: /contact/
author_profile: false
classes: wide
---

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<div class="contact-container">

  <div class="contact-section">
    <div class="contact-label">Email</div>
    <div class="contact-value">
      <a href="mailto:ekmekcic@mcmaster.ca">ekmekcic@mcmaster.ca</a>
    </div>
  </div>

  <div class="contact-section">
    <div class="contact-label">Phone</div>
    <div class="contact-value">(905) 525-9140 x 28964</div>
  </div>

  <div class="contact-section">
    <div class="contact-label">Office</div>
    <div class="contact-value">
      DeGroote School of Business, DSB 413<br>
      McMaster University<br>
      1280 Main Street West<br>
      Hamilton, ON L8S 4L8, Canada
    </div>
  </div>

  <div class="contact-section">
    <div class="contact-label">Office Hours</div>
    <div class="contact-value">By appointment</div>
  </div>

</div>

<script>
(function () {
  // ── Filter logic ──
  var filterBtns = document.querySelectorAll('.pubs-filter');
  var sections   = document.querySelectorAll('.pubs-section');

  filterBtns.forEach(function (btn) {
    btn.addEventListener('click', function () {
      filterBtns.forEach(function (b) { b.classList.remove('active'); });
      btn.classList.add('active');
      var f = btn.getAttribute('data-f');

      sections.forEach(function (s) {
        if (f === 'all') {
          s.style.display = '';
        } else {
          s.style.display = (s.id === 'ps-' + f) ? '' : 'none';
        }
      });
    });
  });

  // ── Theme transition (matches other pages) ──
  if (window.__themeTransitionPubs) return;
  window.__themeTransitionPubs = true;

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
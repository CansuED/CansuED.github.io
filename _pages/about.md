---
layout: single
permalink: /about/
author_profile: false
classes: wide
redirect_from: 
  - /about.html
---

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<div class="about-container">

  <!-- ── Hero strip ─────────────────────────────────────── -->
  <div class="about-hero">
    <p class="about-eyebrow">Assistant Professor · Information Systems</p>
    <h1 class="about-headline">
      Research at the intersection of<br>
      <span>AI, data & sustainability</span>
    </h1>
    <p class="about-tagline">
      DeGroote School of Business · McMaster University
    </p>
  </div>

  <!-- ── Two-column main ────────────────────────────────── -->
  <div class="about-main">

    <!-- Bio text -->
    <div class="about-content">
      <p>I am an <a href="https://degroote.mcmaster.ca/profiles/ekmekcic/" target="_blank">Assistant Professor of Information Systems</a> in the DeGroote School of Business at McMaster University. I direct the <a href="/lab/"><strong>D^4 Sustainable Futures Lab</strong></a>.</p>

      <p>At McMaster, I lead the <strong>Sustainable Futures Hub</strong> at <a href="https://degroote.mcmaster.ca/about/mclean-centre-for-collaborative-discovery/" target="_blank">The McLean Centre for Collaborative Discovery (MCCD)</a>. I also co-lead the University's efforts to develop and advance the <em>Plenary Health</em> graduate program. I am a member of <a href="https://mira.mcmaster.ca/our-faculty/cansu-ekmekcioglu/" target="_blank">McMaster Institute for Research on Aging (MIRA)</a> and <a href="https://mcrew.ca/" target="_blank">The McMaster Centre for Research on Employment and Work (MCREW)</a>.</p>

      <p>My research examines the use and design of data and digital technologies to foster innovation at the managerial, organizational, and community levels with a particular focus on sustainability.</p>

      <p>My current research explores the role of Artificial Intelligence (AI) in public service delivery. I am the Principal Investigator on an Insight Development Grant funded by the Social Sciences and Humanities Research Council of Canada (SSHRC) and the recipient of several competitive internal grants and awards from McMaster University.</p>

      <p>My academic contributions have been published in venues including <em>Journal of the Association for Information Science and Technology</em>, <em>ACM Transactions on Computer-Human Interaction (TOCHI)</em>, and the <em>Proceedings of the ACM on Human-Computer Interaction</em>. I am the Canada Chapter Lead of <a href="https://www.asist.org/" target="_blank">Association for Information Science and Technology (ASIS&T)</a> in 2025–2026.</p>

      <p>I have a Ph.D. in Information Science from the University of Toronto's <a href="https://ischool.utoronto.ca/" target="_blank">Faculty of Information (iSchool)</a>, a Master's Degree in Media & Communication from Galatasaray University, and a Bachelor's Degree in Political Science and International Relations from Bogazici University. In previous lives, I worked as a consultant on technology initiatives in humanitarian and international development contexts and also managed two companies in insurance and IT.</p>
    </div>

    <!-- Sidebar -->
    <div class="about-sidebar">

      <!-- What's New -->
      <div class="updates-box">
        <div class="updates-header">
          <span class="updates-dot"></span>
          <h3>What's New</h3>
        </div>
        <div class="updates-list">

          <div class="update-item">
            <div class="update-date">December 2025</div>
            <div class="update-content">
              Attending <a href="#">ICIS conference</a> in Nashville!
            </div>
          </div>

          <div class="update-item">
            <div class="update-date">November 2025</div>
            <div class="update-content">
              Organized workshop at <a href="#">ASIS&T 2025</a> titled <a href="https://www.asist.org/meetings-events/am/am25/vulnerable-workshop/" target="_blank">Best Practices for Ethics of Care When Engaging Vulnerable Communities</a>
            </div>
          </div>

          <div class="update-item">
            <div class="update-date">June 2025</div>
            <div class="update-content">
              Awarded <a href="#">SSHRC Insight Development Grant</a> for AI in public services research
            </div>
          </div>

          <div class="update-item">
            <div class="update-date">December 2024</div>
            <div class="update-content">
              Appointed Canada Chapter Lead for <a href="https://www.asist.org/" target="_blank">ASIS&T</a> (2025–2026)
            </div>
          </div>

        </div>
      </div>

      <!-- Affiliations -->
      <div class="affiliations-block">
        <div class="aff-header">Affiliations</div>
        <div class="aff-list">
          <div class="aff-item">
            <a href="https://degroote.mcmaster.ca/about/mclean-centre-for-collaborative-discovery/" target="_blank">McLean Centre for Collaborative Discovery</a>
          </div>
          <div class="aff-item">
            <a href="https://mira.mcmaster.ca/our-faculty/cansu-ekmekcioglu/" target="_blank">McMaster Institute for Research on Aging (MIRA)</a>
          </div>
          <div class="aff-item">
            <a href="https://mcrew.ca/" target="_blank">McMaster Centre for Research on Employment and Work (MCREW)</a>
          </div>
          <div class="aff-item">
            <a href="https://www.asist.org/" target="_blank">Association for Information Science and Technology (ASIS&T)</a>
          </div>
        </div>
      </div>

    </div>
  </div>

</div>

<!-- ============================================================
     PREMIUM THEME TRANSITION
     ─────────────────────────────────────────────────────────────
     Mirrors the homepage transition exactly:
     · View Transitions API  → radial circle sweep from toggle btn
     · CSS class fallback    → smooth 0.85s crossfade (Firefox etc.)
     · prefers-reduced-motion → instant swap, no animation
     ============================================================ -->
<script>
(function () {
  'use strict';

  // Guard: only wire up once per page, even if the script runs twice
  if (window.__themeTransitionAbout) return;
  window.__themeTransitionAbout = true;

  // ── Helpers ──────────────────────────────────────────────────

  function isThemeToggle(el) {
    if (!el) return false;
    var sig = (el.className || '') +
              (el.title     || '') +
              (el.getAttribute('aria-label') || '') +
              (el.innerHTML  || '');
    return /dark|light|theme|color.?scheme|sun|moon|☀|🌙/i.test(sig);
  }

  // ── CSS fallback ──────────────────────────────────────────────
  var fallbackTimer = null;
  function cssTransitionFallback() {
    clearTimeout(fallbackTimer);
    document.documentElement.classList.add('is-theme-transitioning');
    fallbackTimer = setTimeout(function () {
      document.documentElement.classList.remove('is-theme-transitioning');
    }, 950);
  }

  // ── View Transitions interception ─────────────────────────────
  var _replaying = false;

  document.addEventListener('click', function (e) {
    if (_replaying) return;

    var btn = e.target;
    while (btn && btn !== document.documentElement) {
      if (
        (btn.tagName === 'BUTTON' || btn.getAttribute('role') === 'button') &&
        isThemeToggle(btn)
      ) break;
      btn = btn.parentElement;
    }
    if (!btn || btn === document.documentElement) return;

    // Pin the reveal circle to the exact button centre
    var r  = btn.getBoundingClientRect();
    var cx = (r.left + r.width  / 2).toFixed(1) + 'px';
    var cy = (r.top  + r.height / 2).toFixed(1) + 'px';
    document.documentElement.style.setProperty('--vt-x', cx);
    document.documentElement.style.setProperty('--vt-y', cy);

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

  }, true /* capture phase */);

  // ── Keyboard support ─────────────────────────────────────────
  document.addEventListener('keydown', function (e) {
    if (e.key !== ' ' && e.key !== 'Enter') return;
    var btn = document.activeElement;
    if (btn && isThemeToggle(btn)) {
      cssTransitionFallback();
    }
  });

}());
</script>
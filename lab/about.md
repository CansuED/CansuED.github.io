---
layout: lab
title: "D⁴ Sustainable Futures"
permalink: /lab/about/
author_profile: false
classes: wide
---

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<div class="lab-about-container">

  <!-- ── Hero ──────────────────────────────────────────────── -->
  <div class="lab-about-hero">
    <p class="lab-about-eyebrow">D⁴ Sustainable Futures Lab</p>
    <h1 class="lab-about-headline">
      Where Technology<br>
      <span>Meets Purpose</span>
    </h1>
    <p class="lab-about-tagline">
      Investigating how human-centered computing, sustainability, and the public good intersect to create meaningful change
    </p>
  </div>

  <!-- ── Mission intro ─────────────────────────────────────── -->
  <div class="lab-about-intro">
    <p>We investigate the intersections between human-centered computing, sustainability, and the public good. Our research seeks to identify how technology and digitally mediated service infrastructures can improve, protect, or potentially hinder the delivery of sustainable, inclusive, and non-rivalrous public goods and services.</p>
    <p>These include, but are not limited to, social service delivery, disaster response, access to sustainable employment and education opportunities, and defence and security.</p>
  </div>

  <!-- ── The Four D's ───────────────────────────────────────── -->
  <div class="lab-pillars">
    <div class="lab-pillar">
      <div class="pillar-letter">D</div>
      <div class="pillar-body">
        <h3>Digital</h3>
        <p>Exploring how digital infrastructure shapes access, equity, and opportunity across communities</p>
      </div>
    </div>
    <div class="lab-pillar">
      <div class="pillar-letter">D</div>
      <div class="pillar-body">
        <h3>Data</h3>
        <p>Harnessing data responsibly to surface insights that drive sustainable, evidence-informed decisions</p>
      </div>
    </div>
    <div class="lab-pillar">
      <div class="pillar-letter">D</div>
      <div class="pillar-body">
        <h3>Design</h3>
        <p>Centering people in the design of technologies that are ethical, inclusive, and built to last</p>
      </div>
    </div>
    <div class="lab-pillar">
      <div class="pillar-letter">D</div>
      <div class="pillar-body">
        <h3>Development</h3>
        <p>Translating research into real-world solutions that advance the UN Sustainable Development Goals</p>
      </div>
    </div>
  </div>

  <!-- ── Focus streams ─────────────────────────────────────── -->
  <div class="lab-focus-section">

    <div class="lab-focus-header">
      <div class="lab-focus-number">01</div>
      <div class="lab-focus-meta">
        <h2>Interdisciplinary Research</h2>
        <p>Our lab brings together researchers and students from diverse fields including information and computer sciences, engineering, law, sociology, and public health to work on projects related to technology and sustainable development.</p>
        <br />
        <p>
        We combine rigorous research methods with practical applications to address real-world challenges at the intersection of technology and social impact.
        </p>
      </div>
    </div>

    <div class="lab-focus-header">
      <div class="lab-focus-number">02</div>
      <div class="lab-focus-meta">
        <h2>Community &amp; Sector Partnerships</h2>
        <p>We actively seek collaborations with government agencies, international organizations, non-profits, social service providers, and community groups eager to leverage technology in building equitable and resilient futures. Our research is grounded in real partnerships with real impact.</p>
      </div>
    </div>

  </div>

  <!-- ── CTA ───────────────────────────────────────────────── -->
  <div class="lab-about-cta">
    <div class="lab-cta-inner">
      <p class="lab-cta-label">Get Involved</p>
      <h3 class="lab-cta-heading">Interested in collaborating or joining the lab?</h3>
      <p class="lab-cta-body">Whether you are a researcher, student, organization, or community partner - we would love to hear from you!</p>
      <a href="mailto:ekmekcic@mcmaster.ca" class="lab-cta-link">
        Reach out <span class="lab-cta-arrow">→</span>
      </a>
    </div>
  </div>

</div>

<script>
(function () {
  'use strict';
  if (window.__themeTransitionResearch) return;
  window.__themeTransitionResearch = true;

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
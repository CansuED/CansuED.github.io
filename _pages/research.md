---
layout: single
permalink: /research/
author_profile: false
classes: wide
---

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<div class="research-container">

  <!-- ── Hero ──────────────────────────────────────────────── -->
  <div class="research-hero">
    <p class="research-eyebrow">Research Program</p>
    <h1 class="research-headline">
      Technology, Society &amp;<br>
      <span>Sustainable Futures</span>
    </h1>
    <p class="research-tagline">
      Interdisciplinary inquiry at the intersection of information systems, AI, and community wellbeing
    </p>
  </div>

  <!-- ── Intro ─────────────────────────────────────────────── -->
  <div class="research-intro">
    <p>At the heart of my interdisciplinary research are concerns at the intersection of information technologies and sustainability. Sustainability is a crucial moral and existential imperative. As highlighted by the United Nations 2030 Sustainable Development Goals (SDGs), sustainability spans topics including economic growth, innovation, health and wellbeing, poverty, inequality, climate change, natural resource preservation, and biodiversity loss.</p>
    <p>My broad research agenda examines sustainable socio-technical systems. Empirically, I concentrate on organizations and communities and the complex social and ethical interplay surrounding them, shaping their use of information technologies. Methodologically, I draw on mixed methods applied both at the local and global levels.</p>
  </div>

  <!-- ── Methods row ────────────────────────────────────────── -->
  <div class="method-row">
    <span class="method-chip"><i class="fas fa-comments"></i>&nbsp; Qualitative Interviews</span>
    <span class="method-chip"><i class="fas fa-chart-bar"></i>&nbsp; Statistical Analysis</span>
    <span class="method-chip"><i class="fas fa-users"></i>&nbsp; Participant Observation</span>
    <span class="method-chip"><i class="fas fa-archive"></i>&nbsp; Archival Research</span>
    <span class="method-chip"><i class="fas fa-pencil-ruler"></i>&nbsp; Community-Driven Design</span>
  </div>

  <!-- ══════════════════════════════════════════════════════════
       STREAM 01
  ════════════════════════════════════════════════════════════ -->
  <div class="research-stream">

    <div class="stream-header">
      <div class="stream-number">01</div>
      <div class="stream-meta">
        <h2>Sustainable Development, IT in Organizations,<br>Migration &amp; Immigrant Integration</h2>
        <p>In alignment with the 2030 United Nations Sustainable Development Goals, which recognize migration as a powerful driver of sustainable development for migrants, their communities, and the host countries, my research agenda has involved close collaboration with migrant communities, non-profit and humanitarian service organizations, refugee entrepreneurs, startups, and policymakers.</p>
      </div>
    </div>

    <div class="projects-grid">

      <!-- Featured / SSHRC -->
      <div class="project-card card-featured">
        <div class="card-badges">
          <span class="badge badge-funding"><i class="fas fa-award"></i>&nbsp; SSHRC Insight Development Grant</span>
          <span class="badge badge-active">● Active</span>
        </div>
        <h3>GenAI in Non-profit Immigrant-serving Agencies</h3>
        <p>My SSHRC-funded research explores the current state of Generative AI adoption in refugee and immigrant serving agencies across Canada, examining opportunities, barriers, and ethical implications for vulnerable communities in the age of AI.</p>
        <a href="/genai-research/" class="card-cta">Explore Project <span class="cta-arrow">→</span></a>
      </div>

      <!-- MIRA -->
      <div class="project-card">
        <div class="card-badges">
          <span class="badge badge-funding"><i class="fas fa-award"></i>&nbsp; MIRA Funded</span>
          <span class="badge badge-active">● Active</span>
        </div>
        <h3>Platform-based Employment, Senior Immigrants &amp; Mobility</h3>
        <p>This study examines how older immigrants experience and engage with platform-mediated gig work amid changing physical, mental, and technological mobility demands, deepening understanding of aspirations within platform-based gig economies.</p>
      </div>

      <!-- Dissertation — full width -->
      <div class="project-card card-wide">
        <div class="card-badges">
          <span class="badge badge-funding"><i class="fas fa-university"></i>&nbsp; Doctoral Research · University of Toronto</span>
          <span class="badge badge-completed">✓ Completed</span>
        </div>
        <h3>Non-profit Data Management and Sustainable Immigrant Integration</h3>
        <p>Drawing on literatures from information science, data studies, and human-computer interaction, <a href="https://www.proquest.com/docview/3128023344?pq-origsite=gscholar&fromopenview=true&sourcetype=Dissertations%20&%20Theses" target="_blank">my dissertation research</a> at the University of Toronto demonstrates how the sustainable digital transformation of immigrant-serving agencies and the social and economic integration of their newcomer clients into Canadian society are interrelated. Critically, it highlights why promoting the responsible design and use of technologies, including Artificial Intelligence, in settlement service delivery is a necessary step in addressing social and digital inequities and the data privacy needs and challenges of disadvantaged groups. Moreover, my dissertation demonstrates broader challenges impacting the sustainable social and economic integration of new Canadians, including digital inclusion and equitable access to digital literacy and resources.</p>
      </div>

    </div>
  </div>

  <!-- ══════════════════════════════════════════════════════════
       STREAM 02
  ════════════════════════════════════════════════════════════ -->
  <div class="research-stream">

    <div class="stream-header">
      <div class="stream-number">02</div>
      <div class="stream-meta">
        <h2>Sustainability, Digital Inclusion &amp; Communities</h2>
        <p>Another strand of my research focuses on the role of information technologies in promoting sustainable futures for marginalized communities as they navigate structural inequities in health, well-being, and work. I examine pressing questions at both theoretical and practical levels (locally and globally) including the links between information infrastructures and citizenship practices, the information-wise transitions of refugees, and digital humanitarian work.</p>
      </div>
    </div>

    <div class="projects-grid">
      <div class="project-card card-wide card-expanding">
        <div class="expanding-inner">
          <div class="expanding-icon">
            <i class="fas fa-seedling"></i>
          </div>
          <div class="expanding-text">
            <p class="expanding-label">Research Expanding</p>
            <p class="expanding-desc">Projects and publications in this stream are actively developing. Check back for updates, or <a href="mailto:ekmekcic@mcmaster.ca">reach out directly</a> to learn more.</p>
          </div>
        </div>
      </div>
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
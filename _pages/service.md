---
layout: single
permalink: /service/
author_profile: false
classes: wide
---

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<div class="service-container">

  <div class="service-hero">
    <p class="service-eyebrow">Academic Service</p>
    <h1 class="service-headline">
      Contributing to the<br>
      <span>Scholarly Community</span>
    </h1>
    <p class="service-tagline">
      Peer review, program committees, editorial work, and leadership in professional organizations advancing the field.
    </p>
  </div>

  <div class="service-section">
    <div class="section-header">
      <div class="section-number">01</div>
      <div class="section-meta">
        <h2>Grant Reviews &amp; Panels</h2>
        <p>Evaluating research proposals that advance knowledge at the intersection of information systems, technology, and society.</p>
      </div>
    </div>

    <div class="service-grid">
      <div class="service-card card-wide">
        <div class="card-icon"><i class="fas fa-award"></i></div>
        <h3>Social Sciences and Humanities Research Council of Canada (SSHRC)</h3>
        <p class="card-org">Canada's primary federal funding agency for social sciences and humanities research</p>
        <div class="card-badges">
          <span class="badge badge-role"><i class="fas fa-search"></i>&nbsp; Grant Reviewer</span>
          <span class="badge badge-year">2025</span>
        </div>
      </div>
    </div>
  </div>

  <div class="service-section">
    <div class="section-header">
      <div class="section-number">02</div>
      <div class="section-meta">
        <h2>Program Committees, Journals &amp; Conferences</h2>
        <p>Shaping the scholarly conversation through reviewing, program planning, and editorial contributions across top venues in HCI, information science, and computing for social good.</p>
      </div>
    </div>

    <div class="service-grid">

      <div class="service-card">
        <div class="card-icon"><i class="fas fa-laptop-code"></i></div>
        <h3>ACM CHI Conference on Human Factors in Computing Systems</h3>
        <p class="card-org">Premier international conference on human-computer interaction</p>
        <div class="card-badges">
          <span class="badge badge-role">Program Committee</span>
          <span class="badge badge-year">2025</span>
        </div>
      </div>

      <div class="service-card">
        <div class="card-icon"><i class="fas fa-leaf"></i></div>
        <h3>ACM SIGCAS/SIGCHI COMPASS</h3>
        <p class="card-org">Conference on Computing and Sustainable Societies</p>
        <div class="card-badges">
          <span class="badge badge-role">Program Committee</span>
          <span class="badge badge-year">2025</span>
        </div>
      </div>

      <div class="service-card">
        <div class="card-icon"><i class="fas fa-globe"></i></div>
        <h3>ACM CSCW — Computer-Supported Cooperative Work</h3>
        <p class="card-org">Leading venue for research on the intersection of social behavior and computing systems</p>
        <div class="card-badges">
          <span class="badge badge-role">Program Committee</span>
          <span class="badge badge-year">2025</span>
        </div>
      </div>

      <div class="service-card">
        <div class="card-icon"><i class="fas fa-book-open"></i></div>
        <h3>Journal &amp; Conference Reviewing</h3>
        <p class="card-org">Ad-hoc and standing reviewer across top-tier venues</p>
        <div class="review-list">
          <div class="review-entry">
            <span class="review-name">Information Systems Journal</span>
            <span class="review-year">2023–present</span>
          </div>
          <div class="review-entry">
            <span class="review-name">Information &amp; Management</span>
            <span class="review-year">2023–present</span>
          </div>
          <div class="review-entry">
            <span class="review-name">Government Information Quarterly</span>
            <span class="review-year">2024–present</span>
          </div>
          <div class="review-entry">
            <span class="review-name">Journal of the Association for Information Science and Technology</span>
            <span class="review-year">2024–present</span>
          </div>
        </div>
      </div>

    </div>
  </div>

  <div class="service-section">
    <div class="section-header">
      <div class="section-number">03</div>
      <div class="section-meta">
        <h2>Leadership &amp; Professional Organizations</h2>
        <p>Building scholarly community and advancing disciplinary conversations through elected and appointed leadership roles.</p>
      </div>
    </div>

    <div class="service-grid">

      <div class="service-card">
        <div class="card-icon"><i class="fas fa-users"></i></div>
        <h3>Association for Information Science and Technology (ASIS&amp;T)</h3>
        <p class="card-org">Canada Chapter Lead — national leadership of a premier information science professional society</p>
        <div class="card-badges">
          <span class="badge badge-leadership"><i class="fas fa-star"></i>&nbsp; Chapter Lead</span>
          <span class="badge badge-active">● Active</span>
          <span class="badge badge-year">2025–2026</span>
        </div>
      </div>

      <div class="service-card">
        <div class="card-icon"><i class="fas fa-chalkboard-teacher"></i></div>
        <h3>Faculty of Information, University of Toronto</h3>
        <p class="card-org">Doctoral student representative contributing to departmental governance and community</p>
        <div class="card-badges">
          <span class="badge badge-leadership">Student Rep</span>
          <span class="badge badge-year">2021–2024</span>
        </div>
      </div>

    </div>
  </div>

</div>

<script>
(function () {
  if (window.__themeTransition) return;
  window.__themeTransition = true;

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
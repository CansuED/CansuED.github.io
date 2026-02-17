---
layout: single
permalink: /
title: ""
author_profile: false
classes: wide
---

<div class="particles" id="particles"></div>

<div class="homepage-content">
  <img src="/images/Cansu.jpeg" alt="Cansu Ekmekcioglu" class="profile-image">

  <h1>Cansu Ekmekcioglu</h1>

  <div class="subtitle">
    Assistant Professor of Information Systems<br>
    DeGroote School of Business, McMaster University
  </div>

  <div class="social-links">
    <a href="mailto:ekmekcic@mcmaster.ca" aria-label="Email">
      <i class="fas fa-envelope"></i>
    </a>
    <a href="https://twitter.com/Cansu_ED" target="_blank" rel="noopener" aria-label="Twitter">
      <i class="fab fa-twitter"></i>
    </a>
    <a href="https://www.linkedin.com/in/cansu-ekmekcioglu/" target="_blank" rel="noopener" aria-label="LinkedIn">
      <i class="fab fa-linkedin"></i>
    </a>
    <a href="https://github.com/CansuED" target="_blank" rel="noopener" aria-label="GitHub">
      <i class="fab fa-github"></i>
    </a>
    <a href="https://scholar.google.ca/citations?user=piapLkEAAAAJ&hl=en" target="_blank" rel="noopener" aria-label="Google Scholar">
      <i class="fas fa-graduation-cap"></i>
    </a>
  </div>
</div>

<script>
(function() {
  function createParticles() {
    const particlesContainer = document.getElementById('particles');
    if (!particlesContainer) {
      setTimeout(createParticles, 100);
      return;
    }
    
    particlesContainer.innerHTML = '';
    const particleCount = 20;
    
    for (let i = 0; i < particleCount; i++) {
      const particle = document.createElement('div');
      particle.className = 'particle';
      const size = Math.random() * 6 + 3;
      const startX = Math.random() * 100;
      const startY = Math.random() * 100;
      const delay = Math.random() * 20;
      particle.style.width = size + 'px';
      particle.style.height = size + 'px';
      particle.style.left = startX + '%';
      particle.style.top = startY + '%';
      particle.style.animationDelay = delay + 's';
      particlesContainer.appendChild(particle);
    }
  }
  
  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', createParticles);
  } else {
    createParticles();
  }
  
  setTimeout(createParticles, 500);
})();
</script>
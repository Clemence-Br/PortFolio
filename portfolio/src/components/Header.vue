<template>
  <header class="header">
    <nav class="nav">
      <div class="logo">
        <span class="logo-dot"></span>
        Clémence Boucher
      </div>
      <ul class="nav-links">
        <li><a href="#about" class="nav-link-item">Qui suis-je ?</a></li>
        <li><a href="#stack" class="nav-link-item">Stack</a></li>
        <li><a href="#experience" class="nav-link-item">Parcours</a></li>
        <li><a href="#projects" class="nav-link-item">Projets</a></li>
      </ul>
    </nav>
  </header>
</template>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: rgba(7, 7, 16, 0.85);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.04);
  z-index: 100;
}

.nav {
  max-width: var(--max-width);
  margin: 0 auto;
  padding: 1.25rem 1.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

@media (min-width: 768px) {
  .nav {
    padding: 1.5rem 3rem;
  }
}

.logo {
  font-weight: 800;
  font-size: 0.85rem;
  letter-spacing: 0.15em;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: #ffffff;
}

.logo-dot {
  width: 8px;
  height: 8px;
  border-radius: 9999px;
  background-color: var(--primary-color);
  display: inline-block;
}

.nav-links {
  display: flex;
  list-style: none;
  align-items: center;
  gap: 1.5rem;
}

@media (min-width: 768px) {
  .nav-links {
    gap: 2.5rem;
  }
}

.nav-link-item {
  font-size: 0.85rem;
  font-weight: 500;
  color: var(--text-muted);
  transition: color 0.3s ease;
}

.nav-link-item:hover {
  color: #ffffff;
}
</style>

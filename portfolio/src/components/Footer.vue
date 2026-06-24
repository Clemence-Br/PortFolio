<template>
  <footer class="footer">
    <p class="copyright">© 2026 - Clémence Boucher - Portfolio</p>
    <p class="tech-stack-info">Conçu avec Vue 3 & TypeScript.</p>
  </footer>
</template>

<style scoped>
.footer {
  margin-top: auto;
  padding: 3rem 1.5rem;
  text-align: center;
  border-top: 1px solid rgba(255, 255, 255, 0.05);
}

.copyright {
  font-size: 0.75rem;
  color: var(--text-muted);
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  margin-bottom: 0.5rem;
}

.tech-stack-info {
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.35);
  font-weight: 500;
}
</style>

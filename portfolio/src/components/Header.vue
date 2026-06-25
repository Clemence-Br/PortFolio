<script setup lang="ts">
import { ref } from "vue";

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;

  if (isMenuOpen.value) {
    document.body.style.overflow = "hidden";
  } else {
    document.body.style.overflow = "";
  }
};

const closeMenu = () => {
  isMenuOpen.value = false;
  document.body.style.overflow = "";
};
</script>

<template>
  <header class="header">
    <nav class="nav">
      <div class="logo">
        <span class="logo-dot"></span>
        Clémence Boucher
      </div>

      <!-- Burger button only visible for mobile -->
      <button
        class="burger-btn"
        @click="toggleMenu"
        :class="{ 'is-active': isMenuOpen }"
        aria-label="Menu"
      >
        <span class="burger-line"></span>
        <span class="burger-line"></span>
        <span class="burger-line"></span>
      </button>

      <div class="nav-content" :class="{ 'is-open': isMenuOpen }">
        <ul class="nav-links">
          <li>
            <a href="#about" class="nav-link-item" @click="closeMenu"
              >Qui suis-je ?</a
            >
          </li>
          <li>
            <a href="#stack" class="nav-link-item" @click="closeMenu">Stack</a>
          </li>
          <li>
            <a href="#experience" class="nav-link-item" @click="closeMenu"
              >Parcours</a
            >
          </li>
          <li>
            <a href="#projects" class="nav-link-item" @click="closeMenu"
              >Projets</a
            >
          </li>
        </ul>
      </div>
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
  -webkit-backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.04);
  z-index: 100;
}

.nav {
  max-width: var(--max-width, 1200px);
  margin: 0 auto;
  padding: 1.25rem 1.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-weight: 800;
  font-size: 0.85rem;
  letter-spacing: 0.15em;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: #ffffff;
  z-index: 101;
}

.logo-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: var(--primary-color);
  display: inline-block;
}

/* Burger button for mobile */
.burger-btn {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 24px;
  height: 18px;
  background: transparent;
  border: none;
  cursor: pointer;
  z-index: 101;
}

.burger-line {
  display: block;
  width: 100%;
  height: 2px;
  background-color: #ffffff;
  border-radius: 2px;
  transition:
    transform 0.3s ease,
    opacity 0.3s ease;
}

.burger-btn.is-active .burger-line:nth-child(1) {
  transform: translateY(8px) rotate(45deg);
  background-color: var(--primary-color);
}
.burger-btn.is-active .burger-line:nth-child(2) {
  opacity: 0;
}
.burger-btn.is-active .burger-line:nth-child(3) {
  transform: translateY(-8px) rotate(-45deg);
  background-color: var(--primary-color);
}

.nav-content {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background-color: rgba(7, 7, 16, 0.98);
  backdrop-filter: blur(15px);
  display: flex;
  justify-content: center;
  align-items: center;

  transform: translateY(-100%);
  opacity: 0;
  transition:
    transform 0.4s cubic-bezier(0.16, 1, 0.3, 1),
    opacity 0.4s ease;
}

.nav-content.is-open {
  transform: translateY(0);
  opacity: 1;
}

.nav-links {
  display: flex;
  flex-direction: column;
  list-style: none;
  align-items: center;
  gap: 2.5rem;
}

.nav-link-item {
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--text-muted);
  transition: color 0.3s ease;
}

.nav-link-item:hover,
.nav-link-item:active {
  color: #ffffff;
}

@media (min-width: 768px) {
  .nav {
    padding: 1.5rem 3rem;
  }

  .burger-btn {
    display: none;
  }

  .nav-content {
    position: static;
    height: auto;
    width: auto;
    background-color: transparent;
    transform: none;
    opacity: 1;
    backdrop-filter: none;
  }

  .nav-links {
    flex-direction: row;
    gap: 2.5rem;
  }

  .nav-link-item {
    font-size: 0.85rem;
    font-weight: 500;
  }
}
</style>

<script setup lang="ts">
import profileImage from "../assets/CLEMENCE_B.png";
import CV from "../assets/CV_Clemence_Boucher.pdf";
</script>

<template>
  <section id="intro" class="intro">
    <div class="intro-content">
      <p class="intro-label">Bonjour, je suis Clémence Boucher</p>
      <h1 class="main-title">
        Développeuse <br />
        <span class="accent-text">Logiciel.</span>
      </h1>
      <p class="intro-desc">
        En fin de cursus BUT Informatique et actuellement développeuse Web en
        alternance, j'aime avant tout comprendre les besoins et relever les
        défis techniques qui en découlent. J'apprécie particulièrement la
        recherche de solutions : analyser une problématique, identifier ce qui
        pourrait freiner son aboutissement et trouver une réponse simple,
        efficace et pertinente à travers une application. Cette démarche
        d'analyse et de conception est ce qui me plaît le plus dans le
        développement.
      </p>
      <div class="cta-group">
        <a href="#projects" class="cta-button">Voir mes projets</a>
        <a
          :href="CV"
          class="secondary-button"
          target="_blank"
          rel="noopener noreferrer"
          >Mon CV &rarr;</a
        >
      </div>
    </div>

    <div class="intro-photo">
      <div class="photo-wrapper">
        <img :src="profileImage" alt="Clémence Boucher" class="profile-img" />
        <div class="photo-glow"></div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.intro {
  min-height: 85vh;
  display: grid;
  grid-template-columns: 1.2fr 1fr;
  align-items: center;
  gap: 4rem;
  padding-top: 8rem;
  padding-bottom: 4rem;
}

.intro-content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.intro-label {
  font-family: var(--font-sans);
  color: var(--primary-color);
  margin-bottom: 1.5rem;
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.2em;
}

.main-title {
  font-size: clamp(2.5rem, 7vw, 5.2rem);
  font-weight: 800;
  line-height: 1.05;
  letter-spacing: -0.02em;
  color: #ffffff;
  padding-bottom: 2rem;
}

.sub-title {
  font-size: clamp(2.2rem, 6.5vw, 4.8rem);
  font-weight: 800;
  line-height: 1.05;
  letter-spacing: -0.02em;
  color: #ffffff;
  margin-bottom: 2rem;
}

.accent-text {
  color: var(--primary-color);
}

.intro-desc {
  max-width: 650px;
  color: var(--text-muted);
  font-size: 1.1rem;
  font-weight: 500;
  line-height: 1.7;
  margin-bottom: 2.5rem;
}

.cta-group {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  width: 100%;
}

.cta-button {
  background-color: var(--primary-color);
  color: #070710;
  padding: 1rem 2rem;
  border-radius: 12px;
  font-weight: 700;
  font-size: 0.95rem;
  transition:
    background-color 0.3s ease,
    transform 0.2s ease;
}

.cta-button:hover {
  background-color: #c4a8ff;
  transform: translateY(-2px);
}

.secondary-button {
  border: 1px solid rgba(255, 255, 255, 0.15);
  color: #ffffff;
  padding: 1rem 2rem;
  border-radius: 12px;
  font-weight: 700;
  font-size: 0.95rem;
  transition:
    background-color 0.3s cubic-bezier(0.16, 1, 0.3, 1),
    border-color 0.3s ease,
    transform 0.2s ease;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
}

.secondary-button:hover {
  background-color: rgba(255, 255, 255, 0.04);
  border-color: rgba(255, 255, 255, 0.3);
  transform: translateY(-2px);
}

.intro-photo {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}

.photo-wrapper {
  position: relative;
  width: 100%;
  max-width: 360px;
  aspect-ratio: 4/5;
  border-radius: 24px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  overflow: hidden;
  background: linear-gradient(
    135deg,
    rgba(32, 28, 56, 0.5),
    rgba(13, 16, 36, 0.5)
  );
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
  transition:
    border-color 0.3s ease,
    transform 0.3s ease;
}

.photo-wrapper:hover {
  border-color: rgba(180, 144, 255, 0.4);
  transform: translateY(-5px);
}

.profile-img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: 2;
  filter: grayscale(15%) contrast(105%);
  transition:
    filter 0.4s ease,
    transform 0.6s ease;
}

.photo-wrapper:hover .profile-img {
  filter: grayscale(0%) contrast(100%);
  transform: scale(1.03);
}

.photo-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 80%;
  height: 80%;
  background: radial-gradient(circle, var(--primary-color) 0%, transparent 70%);
  opacity: 0.2;
  filter: blur(50px);
  z-index: 1;
  pointer-events: none;
}

@media (max-width: 992px) {
  .intro {
    grid-template-columns: 1fr;
    gap: 3rem;
    text-align: center;
    padding-top: 6rem;
  }

  .intro-content {
    align-items: center;
  }

  .intro-desc {
    margin-left: auto;
    margin-right: auto;
  }

  .cta-group {
    justify-content: center;
  }

  .photo-wrapper {
    max-width: 280px;
  }
}
</style>

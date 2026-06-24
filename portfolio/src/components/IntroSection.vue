<template>
  <section id="intro" class="intro">
    <p class="intro-label">Bonjour, je suis Clémence Boucher</p>
    <h1 class="main-title">
      Développeuse <br />
      <span class="accent-text">Logiciel.</span>
    </h1>
    <p class="intro-desc">
      En fin de cursus BUT Informatique et actuellement développeuse Web en
      alternance. J'apprécie particulièrement la recherche de solutions, j'aime
      analyser un besoin, comprendre ce qui pourrait bloquer et trouver une
      manière simple et efficace d'y répondre à travers une application.
    </p>
    <div class="cta-group">
      <a href="#projects" class="cta-button">Découvrir mes projets</a>
      <a href="#about" class="secondary-button">En savoir plus &rarr;</a>
    </div>
  </section>
</template>

<style scoped>
.intro {
  min-height: 85vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  padding-top: 8rem;
  padding-bottom: 4rem;
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
</style>

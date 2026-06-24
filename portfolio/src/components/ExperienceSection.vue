<script setup lang="ts">
import { ref } from "vue";
import educationIcon from "../assets/icons/experience/education.svg";
import workIcon from "../assets/icons/experience/work.svg";
import pinIcon from "../assets/icons/experience/pin.svg";

const experiences = ref([
  {
    year: "2023",
    title: "Baccalauréat Général",
    subtitle:
      "Spécialités : Mathématiques, Physique-Chimie, Sciences de l'Ingénieur",
    place: "Lycée Freppel Obernai",
    type: "education",
    isFuture: false,
  },
  {
    year: "2023 - 2026",
    title: "BUT Informatique",
    subtitle:
      "Option : Réalisation d'applications (conception, développement, validation)",
    place: "IUT Robert Schuman",
    type: "education",
    isFuture: false,
  },
  {
    year: "Avril 2025 - Juin 2025",
    title: "Stage en Développement Web",
    subtitle:
      "Développement de solutions web dédiée à la supervision des réseaux de bornes de recharge électrique et à la gestion de leurs utilisateurs.",
    place: "Freshmile",
    type: "work",
    isFuture: false,
  },
  {
    year: "2025 - 2026",
    title: "Alternance en Développement Web",
    subtitle:
      "Développement et amélioration de solutions web dédiée à la supervision des réseaux de bornes de recharge électrique et à la gestion de leurs utilisateurs.",
    place: "Freshmile",
    type: "work",
    isFuture: false,
  },
  {
    year: "2026 - 2029",
    title: "Diplôme d'ingénieur en Informatique",
    subtitle: "Option Systèmes d'Information",
    place: "CNAM",
    type: "education",
    isFuture: true,
  },
]);
</script>

<template>
  <section id="experience" class="experience-section">
    <h2 class="section-title"><span class="number">03.</span> Mon Parcours</h2>
    <p class="section-description">
      De mes bases universitaires à mon projet de spécialisation en ingénierie,
      voici la trajectoire de mon évolution professionnelle.
    </p>

    <div class="roadmap">
      <div class="roadmap-line"></div>

      <div
        v-for="(item, index) in experiences"
        :key="index"
        class="roadmap-item"
        :class="[
          index % 2 === 0 ? 'left-side' : 'right-side',
          { 'future-item': item.isFuture },
        ]"
      >
        <div class="roadmap-marker">
          <div class="marker-pulse"></div>
          <div class="marker-core"></div>
        </div>

        <div class="roadmap-content">
          <div class="roadmap-header">
            <span class="roadmap-year">{{ item.year }}</span>

            <div class="roadmap-icon" v-if="item.type === 'work'">
              <img :src="workIcon" alt="Work Icon" width="16" height="16" />
            </div>
            <div class="roadmap-icon" v-if="item.type === 'education'">
              <img
                :src="educationIcon"
                alt="Education Icon"
                width="16"
                height="16"
              />
            </div>
          </div>

          <h3 class="roadmap-title">{{ item.title }}</h3>
          <p class="roadmap-subtitle" v-if="item.subtitle">
            {{ item.subtitle }}
          </p>

          <div class="roadmap-place" v-if="item.place">
            <img :src="pinIcon" alt="Location Icon" width="16" height="16" />
            {{ item.place }}
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.experience-section {
  padding: 6rem 0;
  border-top: 1px solid rgba(255, 255, 255, 0.05);
}

.section-title {
  font-size: clamp(1.8rem, 4vw, 2.2rem);
  font-weight: 800;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  letter-spacing: -0.01em;
}

.number {
  font-family: var(--font-mono);
  color: var(--primary-color);
  margin-right: 0.75rem;
  font-size: clamp(1.2rem, 3vw, 1.5rem);
  font-weight: 500;
}

.section-description {
  color: var(--text-muted);
  font-size: 1.05rem;
  line-height: 1.7;
  margin-bottom: 5rem;
  max-width: 600px;
}

.roadmap {
  position: relative;
  max-width: 1000px;
  margin: 0 auto;
}

.roadmap-line {
  position: absolute;
  left: 50%;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(
    to bottom,
    transparent 0%,
    var(--primary-color) 10%,
    rgba(180, 144, 255, 0.2) 90%,
    transparent 100%
  );
  transform: translateX(-50%);
  z-index: 1;
}

.roadmap-item {
  display: flex;
  position: relative;
  margin-bottom: 4rem;
  width: 100%;
  pointer-events: none;
}

.roadmap-item.right-side {
  justify-content: flex-end;
  padding-left: 50%;
}

.roadmap-item.left-side {
  justify-content: flex-start;
  padding-right: 50%;
}

.roadmap-marker {
  position: absolute;
  left: 50%;
  top: 2rem;
  transform: translate(-50%, -50%);
  width: 24px;
  height: 24px;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 5;
  pointer-events: auto;
}

.marker-core {
  width: 12px;
  height: 12px;
  background: var(--bg-color);
  border: 2px solid var(--primary-color);
  border-radius: 50%;
  z-index: 2;
  transition: all 0.3s ease;
}

.marker-pulse {
  position: absolute;
  width: 100%;
  height: 100%;
  background: var(--primary-color);
  border-radius: 50%;
  opacity: 0.3;
  animation: pulse 2.5s infinite cubic-bezier(0.455, 0.03, 0.515, 0.955);
}

@keyframes pulse {
  0% {
    transform: scale(0.8);
    opacity: 0.5;
  }
  100% {
    transform: scale(2.5);
    opacity: 0;
  }
}

.roadmap-content {
  width: 88%;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 255, 255, 0.05);
  border-radius: 16px;
  padding: 1.8rem;
  backdrop-filter: blur(10px);
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  position: relative;
  z-index: 10;
  pointer-events: auto;
}

.roadmap-content::before {
  content: "";
  position: absolute;
  top: 1.5rem;
  width: 0;
  height: 0;
  border-style: solid;
  transition: border-color 0.4s ease;
}

.right-side .roadmap-content::before {
  left: -12px;
  border-width: 10px 12px 10px 0;
  border-color: transparent rgba(255, 255, 255, 0.05) transparent transparent;
}

.left-side .roadmap-content::before {
  right: -12px;
  border-width: 10px 0 10px 12px;
  border-color: transparent transparent transparent rgba(255, 255, 255, 0.05);
}

.roadmap-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}

.roadmap-year {
  font-family: var(--font-mono);
  font-size: 0.9rem;
  color: var(--primary-color);
  font-weight: 600;
  letter-spacing: 0.05em;
}

.roadmap-icon {
  color: var(--text-muted);
  opacity: 0.7;
}

.roadmap-title {
  color: var(--text-color);
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  letter-spacing: -0.01em;
}

.roadmap-subtitle {
  color: var(--text-muted);
  font-size: 0.95rem;
  line-height: 1.5;
  margin-bottom: 1.2rem;
}

.roadmap-place {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--secondary-color);
  background: rgba(56, 189, 248, 0.08);
  padding: 0.4rem 0.8rem;
  border-radius: 6px;
}

.roadmap-item:hover .roadmap-content {
  transform: translateY(-5px) scale(1.02);
  border-color: rgba(139, 92, 246, 0.4);
  background: rgba(255, 255, 255, 0.04);
  box-shadow: 0 15px 30px -10px rgba(139, 92, 246, 0.15);
}

.roadmap-item:hover .marker-core {
  transform: scale(1.5);
  background-color: var(--primary-color);
  box-shadow: 0 0 15px var(--primary-color);
}

.right-side:hover .roadmap-content::before {
  border-color: transparent rgba(139, 92, 246, 0.4) transparent transparent;
}
.left-side:hover .roadmap-content::before {
  border-color: transparent transparent transparent rgba(139, 92, 246, 0.4);
}

.future-item .roadmap-content {
  border-style: dashed;
  border-color: rgba(56, 189, 248, 0.2);
}

.future-item .marker-core {
  border-color: var(--secondary-color);
}

.future-item .marker-pulse {
  background: var(--secondary-color);
}

.future-item .roadmap-year {
  color: var(--secondary-color);
}

.future-item:hover .roadmap-content {
  border-color: rgba(56, 189, 248, 0.5);
  box-shadow: 0 15px 30px -10px rgba(56, 189, 248, 0.15);
}

.future-item.right-side:hover .roadmap-content::before {
  border-color: transparent rgba(56, 189, 248, 0.5) transparent transparent;
}
.future-item.left-side:hover .roadmap-content::before {
  border-color: transparent transparent transparent rgba(56, 189, 248, 0.5);
}

.future-item:hover .marker-core {
  background-color: var(--secondary-color);
  box-shadow: 0 0 15px var(--secondary-color);
}

@media (max-width: 768px) {
  .roadmap-line {
    left: 20px;
    transform: none;
  }

  .roadmap-item.left-side,
  .roadmap-item.right-side {
    justify-content: flex-end;
    padding-left: 60px;
    padding-right: 0;
  }

  .roadmap-content {
    width: 100%;
  }

  .roadmap-marker {
    left: 20px;
    transform: translate(-50%, -50%);
  }

  .roadmap-item.left-side .roadmap-content::before,
  .roadmap-item.right-side .roadmap-content::before {
    left: -12px;
    right: auto;
    border-width: 10px 12px 10px 0;
    border-color: transparent rgba(255, 255, 255, 0.05) transparent transparent;
  }

  .roadmap-item.left-side:hover .roadmap-content::before,
  .roadmap-item.right-side:hover .roadmap-content::before {
    border-color: transparent rgba(139, 92, 246, 0.4) transparent transparent;
  }

  .future-item.left-side:hover .roadmap-content::before,
  .future-item.right-side:hover .roadmap-content::before {
    border-color: transparent rgba(56, 189, 248, 0.5) transparent transparent;
  }
}
</style>

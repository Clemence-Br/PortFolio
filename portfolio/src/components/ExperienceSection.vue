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
    <h3 class="section-title"><span class="number">03.</span> Mon Parcours</h3>
    <p class="section-description">
      De mes bases universitaires à mon projet de spécialisation en ingénierie,
      voici la trajectoire de mon évolution professionnelle.
    </p>

    <div class="timeline">
      <div
        v-for="(item, index) in experiences"
        :key="index"
        class="timeline-item"
        :class="{ 'future-item': item.isFuture }"
      >
        <div class="timeline-marker"></div>

        <div class="timeline-content">
          <div class="timeline-header">
            <span class="timeline-year">{{ item.year }}</span>

            <div class="timeline-icon" v-if="item.type === 'work'">
              <img :src="workIcon" alt="Work Icon" width="16" height="16" />
            </div>

            <div class="timeline-icon" v-if="item.type === 'education'">
              <img
                :src="educationIcon"
                alt="Education Icon"
                width="16"
                height="16"
              />
            </div>
          </div>

          <h4 class="timeline-title">{{ item.title }}</h4>
          <p class="timeline-subtitle" v-if="item.subtitle">
            {{ item.subtitle }}
          </p>

          <div class="timeline-place" v-if="item.place">
            <img :src="pinIcon" alt="Pin Icon" width="14" height="14" />
            {{ item.place }}
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.experience-section {
  padding: 4rem 0;
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
  margin-bottom: 4rem;
  max-width: 600px;
}

.timeline {
  position: relative;
  max-width: 800px;
  margin: 0;
  padding-left: 2.5rem;
}

.timeline::before {
  content: "";
  position: absolute;
  top: 0;
  bottom: 0;
  left: 7px;
  width: 2px;
  background: linear-gradient(
    to bottom,
    var(--primary-color) 0%,
    rgba(180, 144, 255, 0.1) 90%,
    transparent 100%
  );
}

.timeline-item {
  position: relative;
  padding-bottom: 3rem;
}

.timeline-item:last-child {
  padding-bottom: 0;
}

.timeline-marker {
  position: absolute;
  top: 0.25rem;
  left: -2.5rem;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  border: 2px solid var(--primary-color);
  background: var(--bg-color);
  transition: all 0.3s ease;
  z-index: 2;
}

.timeline-content {
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 255, 255, 0.05);
  border-radius: 12px;
  padding: 1.5rem;
  transition:
    transform 0.3s ease,
    border-color 0.3s ease;
}

.timeline-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.75rem;
}

.timeline-year {
  font-family: var(--font-mono);
  font-size: 0.9rem;
  color: var(--primary-color);
  font-weight: 600;
}

.timeline-icon {
  color: var(--text-muted);
  opacity: 0.6;
}

.timeline-title {
  color: var(--text-color);
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.timeline-subtitle {
  color: var(--text-muted);
  font-size: 0.95rem;
  line-height: 1.5;
  margin-bottom: 1rem;
}

.timeline-place {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.85rem;
  font-weight: 500;
  color: var(--secondary-color);
  background: rgba(56, 189, 248, 0.08);
  padding: 0.4rem 0.8rem;
  border-radius: 6px;
}

.timeline-item:hover .timeline-marker {
  background-color: var(--primary-color);
  box-shadow: 0 0 15px rgba(139, 92, 246, 0.5);
  transform: scale(1.2);
}

.timeline-item:hover .timeline-content {
  transform: translateX(5px);
  border-color: rgba(139, 92, 246, 0.3);
  background: rgba(255, 255, 255, 0.04);
}

.future-item .timeline-marker {
  border-color: var(--secondary-color);
  border-style: dashed;
  background: transparent;
}

.future-item .timeline-content {
  border-style: dashed;
  border-color: rgba(255, 255, 255, 0.1);
  background: transparent;
}

.future-item .timeline-year {
  color: var(--secondary-color);
}

.future-item:hover .timeline-marker {
  background-color: var(--secondary-color);
  box-shadow: 0 0 15px rgba(56, 189, 248, 0.5);
}

.future-item:hover .timeline-content {
  border-color: rgba(56, 189, 248, 0.4);
}
</style>

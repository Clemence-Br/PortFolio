<script setup lang="ts">
import type { Project } from "../types";
defineProps<{
  project: Project;
}>();
</script>

<template>
  <article class="project-card group">
    <div class="card-image-wrapper">
      <img
        :src="project.image"
        :alt="project.title"
        class="card-image"
        loading="lazy"
      />
      <div class="hover-glow"></div>
    </div>

    <div class="card-content">
      <div class="tech-tags">
        <span v-for="tech in project.technologies" :key="tech" class="tag">
          {{ tech }}
        </span>
      </div>

      <h4 class="card-title">{{ project.title }}</h4>
      <p class="card-description">{{ project.description }}</p>

      <div class="card-links">
        <a
          v-if="project.githubUrl"
          :target="'_blank'"
          :href="project.githubUrl"
          rel="noopener"
          class="project-link"
        >
          GitHub <span class="arrow">&nearr;</span>
        </a>
        <a
          v-if="project.productionUrl"
          :target="'_blank'"
          :href="project.productionUrl"
          rel="noopener"
          class="project-link"
        >
          Production <span class="arrow">&nearr;</span>
        </a>
      </div>
    </div>
  </article>
</template>

<style scoped>
.project-card {
  display: flex;
  flex-direction: column;
  background: transparent;
  transition: transform 0.3s ease;
}

.card-image-wrapper {
  height: 256px;
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.05);
  position: relative;
  overflow: hidden;
  margin-bottom: 1.5rem;
}

.project-card:hover .card-image-wrapper {
  border-color: rgba(255, 255, 255, 0.12);
}

.card-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.5s ease;
  z-index: 2;
}

.project-card:hover .card-image {
  transform: scale(1.05);
}

.bg-placeholder-title {
  font-size: 0.65rem;
  font-weight: 700;
  letter-spacing: 0.25em;
  color: var(--text-muted);
  text-transform: uppercase;
  opacity: 0.6;
  z-index: 10;
}

.hover-glow {
  position: absolute;
  inset: 0;
  background-color: var(--primary-color);
  opacity: 0;
  transition: opacity 0.4s ease;
  z-index: 5;
}

.project-card:hover .hover-glow {
  opacity: 0.04;
}

.card-content {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.tag {
  font-family: var(--font-sans);
  font-size: 9px;
  font-weight: 700;
  color: var(--text-muted);
  border: 1px solid rgba(255, 255, 255, 0.08);
  padding: 0.35rem 0.65rem;
  border-radius: 6px;
  text-transform: uppercase;
  letter-spacing: 0.15em;
}

.card-title {
  font-size: 1.5rem;
  font-weight: 800;
  margin-bottom: 0.75rem;
  color: #ffffff;
  letter-spacing: -0.01em;
}

.card-description {
  color: var(--text-muted);
  font-size: 0.95rem;
  font-weight: 500;
  line-height: 1.6;
  margin-bottom: 1.5rem;
  flex-grow: 1;
}

.card-links {
  display: flex;
  gap: 1.5rem;
  font-size: 0.75rem;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  margin-top: auto;
}

.project-link {
  color: #ffffff;
  display: inline-flex;
  align-items: center;
  gap: 0.25rem;
  transition: color 0.2s ease;
}

.project-link:hover {
  color: var(--primary-color);
}

.arrow {
  font-size: 0.85rem;
  display: inline-block;
  transition: transform 0.2s ease;
}

.project-link:hover .arrow {
  transform: translate(2px, -2px);
}
</style>

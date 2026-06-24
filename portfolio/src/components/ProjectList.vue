<script setup lang="ts">
import type { Project } from "../types";
import ProjectCard from "./ProjectCard.vue";

defineProps<{
  projects: Project[];
}>();
</script>

<template>
  <section id="projects" class="projects-section">
    <div class="section-header">
      <h3 class="section-title-custom">Projets</h3>
    </div>
    <div class="projects-grid">
      <project-card
        v-for="project in projects"
        :key="project.id"
        :project="project"
      />
    </div>
  </section>
</template>

<style scoped>
.projects-section {
  padding: 6rem 0;
}

.section-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  padding-bottom: 1.25rem;
  margin-bottom: 3rem;
}

.section-title-custom {
  font-size: clamp(1.8rem, 4vw, 2.4rem);
  font-weight: 800;
  color: #ffffff;
  letter-spacing: -0.02em;
}

.projects-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 2.5rem;
}

@media (min-width: 768px) {
  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 2.5rem;
  }
}

@media (min-width: 1200px) {
  .projects-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 2.5rem;
  }
}
</style>

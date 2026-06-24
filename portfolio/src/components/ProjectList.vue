<script setup lang="ts">
import type { Project } from "../types";
import ProjectCard from "./ProjectCard.vue";

defineProps<{
  projects: Project[];
}>();
</script>

<template>
  <section id="projects" class="projects-section">
    <h2 class="section-title"><span class="number">04.</span> Projets</h2>
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

.projects-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 2.5rem;
  margin-top: 2rem;
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

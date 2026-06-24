<script setup lang="ts">
import { ref } from "vue";
import vue from "../assets/icons/stack/vue.svg";
import react from "../assets/icons/stack/react.svg";
import javascript from "../assets/icons/stack/javascript.svg";
import typescript from "../assets/icons/stack/typescript.svg";
import css from "../assets/icons/stack/css.svg";
import html from "../assets/icons/stack/html.svg";
import tailwind from "../assets/icons/stack/tailwind.svg";
import nodejs from "../assets/icons/stack/nodejs.svg";
import php from "../assets/icons/stack/php.svg";
import laravel from "../assets/icons/stack/laravel.svg";
import java from "../assets/icons/stack/java.svg";
import c from "../assets/icons/stack/c.svg";
import csharp from "../assets/icons/stack/csharp.svg";
import mysql from "../assets/icons/stack/mysql.svg";
import git from "../assets/icons/stack/git.svg";
import gitlab from "../assets/icons/stack/gitlab.svg";
import github from "../assets/icons/stack/github.svg";
import azureDevops from "../assets/icons/stack/azure-devops.svg";
import docker from "../assets/icons/stack/docker.svg";
import figma from "../assets/icons/stack/figma.svg";
import vscode from "../assets/icons/stack/vscode.svg";
import postman from "../assets/icons/stack/postman.svg";

const skillCategories = ref([
  {
    name: "Langages & Frameworks",
    skills: [
      { name: "Vue.js", icon: vue },
      { name: "React", icon: react },
      { name: "React Native", icon: react },
      { name: "JavaScript", icon: javascript },
      { name: "TypeScript", icon: typescript },
      { name: "CSS", icon: css },
      { name: "HTML", icon: html },
      { name: "Tailwind CSS", icon: tailwind },
      { name: "Node.js", icon: nodejs },
      { name: "PHP", icon: php },
      { name: "Laravel", icon: laravel },
      { name: "Java", icon: java },
      { name: "C", icon: c },
      { name: "C#", icon: csharp },
      { name: "MySQL", icon: mysql },
    ],
  },
  {
    name: "Outils",
    skills: [
      { name: "Git", icon: git },
      { name: "GitLab", icon: gitlab },
      { name: "GitHub", icon: github },
      { name: "Azure DevOps", icon: azureDevops },
      { name: "Docker", icon: docker },
      { name: "Figma", icon: figma },
      { name: "VS Code", icon: vscode },
      { name: "Postman", icon: postman },
    ],
  },
]);
</script>

<template>
  <div class="tech-stack-section">
    <h2 class="tech-main-title"><span class="number">02.</span> Stack</h2>
    <p class="tech-description">
      Voici les technologies avec lesquelles je travaille au quotidien et/ou que
      j'ai acquises, tant par mon cursus à l'IUT que par mon expérience en
      entreprise.
    </p>

    <div class="categories-container">
      <div
        v-for="category in skillCategories"
        :key="category.name"
        class="tech-category"
      >
        <h3 class="category-name">{{ category.name }}</h3>

        <div class="marquee-wrapper">
          <div class="marquee-content">
            <!-- First iteration of the skills for the infinite loop -->
            <div class="tech-tags marquee-tags">
              <div
                v-for="skill in category.skills"
                :key="skill.name"
                class="tag"
              >
                <img
                  :src="skill.icon"
                  :alt="`${skill.name} icon`"
                  class="skill-icon"
                />
                <span>{{ skill.name }}</span>
              </div>
            </div>

            <!-- Second iteration (Exact copy for the infinite loop) -->
            <div class="tech-tags marquee-tags" aria-hidden="true">
              <div
                v-for="skill in category.skills"
                :key="'dup-' + skill.name"
                class="tag"
              >
                <img
                  :src="skill.icon"
                  :alt="`${skill.name} icon`"
                  class="skill-icon"
                />
                <span>{{ skill.name }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.tech-stack-section {
  padding: 4rem 0;
  border-top: 1px solid rgba(255, 255, 255, 0.05);
}

.tech-main-title {
  font-size: clamp(1.6rem, 3vw, 2rem);
  font-weight: 800;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  letter-spacing: -0.01em;
  color: #ffffff;
}

.number {
  font-family: var(--font-mono);
  color: var(--primary-color);
  margin-right: 0.75rem;
  font-size: clamp(1.1rem, 2.5vw, 1.4rem);
  font-weight: 500;
}

.tech-description {
  color: var(--text-muted);
  font-size: 1.05rem;
  line-height: 1.7;
  margin-bottom: 3rem;
  max-width: 600px;
}

.categories-container {
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
}

.tech-category {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.category-name {
  color: #ffffff;
  font-size: 1.1rem;
  font-weight: 700;
  letter-spacing: 0.02em;
}

.tag {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-family: var(--font-sans);
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--text-muted);
  border: 1px solid rgba(255, 255, 255, 0.08);
  padding: 0.5rem 0.85rem;
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.02);
  transition: all 0.2s ease;
  white-space: nowrap;
}

.tag:hover {
  border-color: rgba(255, 255, 255, 0.2);
  color: #ffffff;
  background: rgba(255, 255, 255, 0.05);
  transform: translateY(-2px);
}

.skill-icon {
  width: 18px;
  height: 18px;
  object-fit: contain;
}

/* Style for the marquee effect */
.marquee-wrapper {
  width: 100%;
  overflow: hidden;
  padding: 0.5rem 0;
  mask-image: linear-gradient(
    to right,
    transparent,
    black 5%,
    black 95%,
    transparent
  );
  -webkit-mask-image: linear-gradient(
    to right,
    transparent,
    black 5%,
    black 95%,
    transparent
  );
}

.marquee-content {
  display: flex;
  gap: 0.85rem;
  width: max-content;
  animation: scroll 60s linear infinite;
}

.marquee-content:hover {
  animation-play-state: paused;
}

.marquee-tags {
  display: flex;
  flex-wrap: nowrap;
  gap: 0.85rem;
}

/* Keyframe animation: shift the entire content by exactly half of its width */
@keyframes scroll {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(calc(-50% - 0.425rem));
  }
}
</style>

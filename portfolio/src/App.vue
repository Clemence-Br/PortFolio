<script setup lang="ts">
import { ref } from "vue";
import type { Project } from "./types";
import Header from "./components/Header.vue";
import IntroSection from "./components/IntroSection.vue";
import AboutSection from "./components/AboutSection.vue";
import TechStack from "./components/TechStack.vue";
import ExperienceSection from "./components/ExperienceSection.vue";
import ProjectList from "./components/ProjectList.vue";
import Footer from "./components/Footer.vue";
import straseventImage from "./assets/projects/strasevent.png";
import onofImage from "./assets/projects/onof.png";
import supervisionImage from "./assets/projects/supervision.png";
import pookemonImage from "./assets/projects/pookemon.png";
import snakeImage from "./assets/projects/snake.png";
import labyrintheImage from "./assets/projects/labyrinthe.png";

const projects = ref<Project[]>([
  {
    id: 1,
    title: "StrasEvent (BUT3)",
    description:
      "Solution complète de gestion d'événements pour l'Eurométropole de Strasbourg, comprenant une application de bureau et son application mobile compagnon. Projet d'envergure mené en équipe de six, axé sur la synchronisation et l'expérience utilisateur.",
    image: straseventImage,
    technologies: [
      "React",
      "React Native",
      "JavaScript",
      "Leaflet",
      "Node.js",
      "Express",
      "Prisma",
      "SQLite",
    ],
    githubUrl: "https://github.com/Clemence-Br/StrasEvent",
  },
  {
    id: 2,
    title: "O'nof (BUT2)",
    description:
      "Serious Game présentant les enjeux de la création de formations universitaires sous forme de jeu de cartes.",
    image: onofImage,
    technologies: ["React", "JavaScript"],
    githubUrl: "https://github.com/Clemence-Br/O-nof",
  },
  {
    id: 3,
    title: "Applications de Supervision (Freshmile)",
    description:
      "Participation au développement d'applications de supervision pour la gestion des bornes de recharge électriques et de leurs utilisateurs. J'ai notamment travaillé sur le système tarifaire des solutions.",
    image: supervisionImage,
    technologies: ["Vue 2/3", "TypeScript", "Laravel 10"],
    githubUrl: "",
  },
  {
    id: 4,
    title: "Pookemon (BUT1)",
    description:
      "Jeu de cartes inspiré de Pokémon où un joueur humain fait face à l'ordinateur. Le gagnant est celui qui parvient à éliminer tous les Pokémons de son adversaire.",
    image: pookemonImage,
    technologies: ["Java", "UML"],
    githubUrl: "https://github.com/Clemence-Br/POOkemon",
  },
  {
    id: 5,
    title: "Snake (BUT1)",
    description:
      "Snake développé en assembleur MIPS32, où le joueur contrôle un serpent qui grandit à chaque fruit mangé. Le jeu se termine si le serpent se mord la queue ou touche les murs.",
    image: snakeImage,
    technologies: ["MIPS32"],
    githubUrl: "https://github.com/Clemence-Br/Snake",
  },
  {
    id: 6,
    title: "Labyrinthe (BUT2)",
    description:
      "Jeu du labyrinthe en 2d où les joueurs s'affrontent pour récupérer des trésors en se frayant un chemin à travers les tuiles mouvantes.",
    image: labyrintheImage,
    technologies: ["Java", "Swing", "UML"],
    githubUrl: "https://github.com/Clemence-Br/Labyrinthe",
  },
]);
</script>

<template>
  <div class="app-container">
    <div class="gradient-bg">
      <div class="gradient-blob blob-1"></div>
      <div class="gradient-blob blob-2"></div>
      <div class="gradient-blob blob-3"></div>
      <div class="noise-overlay"></div>
    </div>

    <Header />
    <main class="main-content">
      <IntroSection />
      <AboutSection />
      <TechStack />
      <ExperienceSection />
      <ProjectList :projects="projects" />
    </main>
    <Footer />
  </div>
</template>

<style>
.app-container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.main-content {
  max-width: var(--max-width);
  margin: 0 auto;
  padding: 0 2rem;
  width: 100%;
}

@media (min-width: 768px) {
  .main-content {
    padding: 0 3rem;
  }
}

.gradient-bg {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: 0;
  pointer-events: none;
  overflow: hidden;
}

.gradient-blob {
  position: absolute;
  filter: blur(90px);
  opacity: 0.2;
  border-radius: 50%;
  animation: blob-move 10s infinite alternate cubic-bezier(0.4, 0, 0.2, 1);
  will-change: transform;
}

.blob-1 {
  top: -10%;
  left: -10%;
  width: 45vw;
  height: 45vw;
  background-color: #8558e7;
  animation-delay: 1s;
}

.blob-2 {
  bottom: -20%;
  right: -10%;
  width: 50vw;
  height: 50vw;
  background-color: #0b0f7e;
  animation-delay: -5s;
}

.blob-3 {
  top: 40%;
  left: 30%;
  width: 45vw;
  height: 45vw;
  background-color: #4c0d80;
  animation-duration: 25s;
  animation-delay: -10s;
}

@keyframes blob-move {
  0% {
    transform: translate(0, 0) scale(1);
  }
  33% {
    transform: translate(10%, 15%) scale(1.1);
  }
  66% {
    transform: translate(-15%, 10%) scale(0.9);
  }
  100% {
    transform: translate(15%, -10%) scale(1.05);
  }
}
</style>

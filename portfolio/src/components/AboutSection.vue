<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";
import photo1 from "../assets/photos_carousel/photo1.jpg";
import photo2 from "../assets/photos_carousel/photo2.jpg";
import photo3 from "../assets/photos_carousel/photo3.jpg";
import photo4 from "../assets/photos_carousel/photo4.jpg";

const photos = ref([photo1, photo2, photo3, photo4]);

const currentIndex = ref(0);
let intervalId: ReturnType<typeof setInterval>;

onMounted(() => {
  // Change the photo every 5 seconds
  intervalId = setInterval(() => {
    currentIndex.value = (currentIndex.value + 1) % photos.value.length;
  }, 5000);
});

onUnmounted(() => {
  clearInterval(intervalId);
});
</script>

<template>
  <section id="about" class="about-section">
    <h2 class="section-title"><span class="number">01.</span> Qui suis-je ?</h2>

    <div class="about-grid">
      <div class="about-text">
        <p>
          Mon parcours à l'IUT Robert Schuman (BUT Informatique, option
          Réalisation d'applications) m'a donné de bonnes bases techniques, mais
          c'est en entreprise que j'ai vraiment confirmé mon intérêt pour le
          développement web. J'intégrerais à partir de septembre 2026 la
          formation d'ingénieur en Informatique et Systèmes d'information du
          CNAM afin de perfectionner mes compétences et d'acquérir des
          connaissances plus approfondies dans le domaine. Aujourd'hui, j'évolue
          en alternance dans l'entreprise Freshmile, où je continuerai de
          m'investir pour les 3 années à venir.
        </p>
        <p>
          En dehors du développement, je pratique le handball depuis plus de dix
          ans et je suis une grande fan d'escape games. Ces activités m'ont
          appris à travailler en équipe, à garder un esprit analytique et à
          communiquer efficacement, même dans des situations tendues.
        </p>
      </div>

      <div class="photo-container">
        <div class="photo-wrapper">
          <transition name="fade">
            <img
              :key="currentIndex"
              :src="photos[currentIndex]"
              alt="Photo"
              class="photo-img"
            />
          </transition>
          <div class="photo-glow"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-section {
  padding: 4rem 0;
  border-top: 1px solid rgba(255, 255, 255, 0.05);
}

.about-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 3.5rem;
  align-items: center;
}

@media (min-width: 992px) {
  .about-grid {
    grid-template-columns: 3fr 2fr;
    gap: 5rem;
  }
}

.about-text p {
  color: var(--text-muted);
  font-size: 1.05rem;
  line-height: 1.75;
  margin-bottom: 1.5rem;
  font-weight: 500;
}

.photo-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

.photo-wrapper {
  position: relative;
  width: 100%;
  max-width: 300px;
  aspect-ratio: 1/1;
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  overflow: hidden;
  background: linear-gradient(
    135deg,
    var(--card-grad-start, #201c38),
    var(--card-grad-end, #0d1024)
  );
  transition: border-color 0.3s ease;
}

.photo-wrapper:hover {
  border-color: rgba(180, 144, 255, 0.3);
}

.photo-img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: contain;
  z-index: 2;
  filter: grayscale(20%) contrast(110%);
  transition:
    filter 0.3s ease,
    transform 0.5s ease;
}

.photo-wrapper:hover .photo-img {
  filter: grayscale(0%) contrast(100%);
  transform: scale(1.02);
}

.photo-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 80%;
  height: 80%;
  background: radial-gradient(circle, var(--primary-color) 0%, transparent 70%);
  opacity: 0.15;
  filter: blur(40px);
  z-index: 1;
  pointer-events: none;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>

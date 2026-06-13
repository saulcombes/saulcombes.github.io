---
layout: default
---

<div id="loader">
  <img src="/assets/img/bacteria.png" alt="loading icon" class="loader-icon">
</div>

<!-- PETRI DISH NAVIGATION -->
<style>
/* --- PETRI DISH NAVIGATION --- */

.petri-nav {
  position: fixed;
  right: 40px;
  top: 50%;
  transform: translateY(-50%);
  width: 220px;
  height: 220px;
  border: 3px solid rgba(120,160,220,0.35); /* soft blue ring */
  border-radius: 50%;
  backdrop-filter: blur(2px);
  z-index: 50;
}

/* Colony nodes */
.petri-colony {
  position: absolute;
  width: 26px;
  height: 26px;
  background: #4a7bd1; /* primary blue */
  border-radius: 50%;
  cursor: pointer;
  transition: 0.25s ease;
  box-shadow: 0 0 0 rgba(140,180,255,0.4);
}

/* Hover effect */
.petri-colony:hover {
  transform: scale(1.18);
  box-shadow: 0 0 12px rgba(140,180,255,0.7);
}

/* Colony labels */
.petri-colony::after {
  content: attr(data-label);
  position: absolute;
  left: 35px;
  top: 50%;
  transform: translateY(-50%);
  background: white;
  padding: 4px 8px;
  border-radius: 6px;
  font-size: 0.8rem;
  opacity: 0;
  pointer-events: none;
  transition: 0.25s ease;
  white-space: nowrap;
  border: 1px solid rgba(0,0,0,0.1);
}

.petri-colony:hover::after {
  opacity: 1;
}

/* --- COLONY POSITIONS (4 nodes) --- */
.colony-home      { top: 20%; left: 50%; transform: translateX(-50%); }
.colony-projects  { top: 50%; left: 80%; transform: translateY(-50%); }
.colony-research  { top: 75%; left: 50%; transform: translateX(-50%); }
.colony-skills    { top: 50%; left: 20%; transform: translateY(-50%); }

/* --- SHIFT MAIN CONTENT LEFT TO BALANCE LAYOUT --- */
.main-content {
  margin-right: 260px; /* space for the dish */
}
</style>

<div class="petri-nav">
  <a href="/" class="petri-colony colony-home" data-label="Home"></a>
  <a href="/Projects/Projects" class="petri-colony colony-projects" data-label="Projects"></a>
  <a href="/Research_Areas" class="petri-colony colony-research" data-label="Research Areas"></a>
  <a href="/Skills" class="petri-colony colony-skills" data-label="Skills"></a>
</div>

<style>
.carousel-container {
  width: 100%;
  overflow: hidden;
  margin: 3rem auto;
  padding: 4rem 0;
  position: relative;
}

/* Fade-out edges */
.carousel-container::before,
.carousel-container::after {
  content: "";
  position: absolute;
  top: 0;
  width: 180px;
  height: 100%;
  pointer-events: none;
  z-index: 10;
}

.carousel-container::before {
  left: 0;
  background: linear-gradient(to right, rgba(255,255,255,1), rgba(255,255,255,0));
}

.carousel-container::after {
  right: 0;
  background: linear-gradient(to left, rgba(255,255,255,1), rgba(255,255,255,0));
}

.carousel-track {
  display: flex;
  gap: 2rem;
  transition: transform 0.6s ease;
  will-change: transform;
}

.carousel-card {
  min-width: 300px;
  min-height: 400px;
  height: auto;
  padding: 1.5rem;
  border-radius: 22px;
  backdrop-filter: blur(14px);
  background: rgba(255, 255, 255, 0.25);
  border: 1px solid rgba(255, 255, 255, 0.35);
  box-shadow: 0 10px 30px rgba(0,0,0,0.15);
  cursor: pointer;
  transition: transform 0.4s ease, opacity 0.4s ease;
  opacity: 0.4;
  transform: scale(0.85);
}

.carousel-card.active {
  transform: scale(1.15);
  opacity: 1;
}

.carousel-card:hover {
  box-shadow:
    0 20px 45px rgba(0,0,0,0.25),
    0 0 25px rgba(255,255,255,0.4) inset;
}

.carousel-card.active:hover {
  transform: scale(1.2) translateY(-8px) rotateX(4deg) rotateY(4deg);
}

.carousel-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Fullscreen loader */
#loader {
  position: fixed;
  inset: 0;
  background: white;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
  transition: opacity 0.4s ease;
}

/* Elegant spin → pause → spin → pause */
.loader-icon {
  width: 60px;
  height: 60px;
  opacity: 0.85;
  animation: gentleSpin 2.4s ease-in-out infinite;
}

@keyframes gentleSpin {
  0%   { transform: rotate(0deg); }
  40%  { transform: rotate(360deg); }
  60%  { transform: rotate(360deg); }
  100% { transform: rotate(360deg); }
}

/* Fade-out when page is ready */
#loader.fade-out {
  opacity: 0;
  pointer-events: none;
}
</style>

<div class="main-content">

# Saul Combes  
### Cellular and Molecular Medicine MSc

I integrate Mechanistic Biology, Clinical Data, and Computational Methods to understand infection and injury.

---

<h2>Active Projects</h2>

<div class="carousel-container">
  <div class="carousel-wrapper">
    <div class="carousel-track">

      <div class="carousel-card" data-link="/Projects/GWAS">
        <h3>Genome Wide Association Study - Supervised - In Progress</h3>
        <p>Data Science • Clinical Informatics • Genomics</p>
        <p>-----</p>
        <p>A Genome Wide Association Study using Mendelian randomisation with infectious disease as an outcome as part of an MRC-IEU supervised project.</p>
      </div>

      <div class="carousel-card" data-link="/Projects/Communication">
        <h3>From superbugs to scapegoats: Could antimicrobial resistance misinformation fuel xenophobic discourse?</h3>
        <p>Public Health • Scientific Communication • AMR</p>
        <p>-----</p>
        <p>A commentary piece warning of a foreseeable risk of AMR communication being manipulated to disseminate xenophobic rhetoric, detailing the role of medical scientists to preserve public understanding.</p>
      </div>

      <div class="carousel-card" data-link="/Projects/QSI_Review">
        <h3>QSI use targeting Pseudomonas aeruginosa in an Intensive Care Setting</h3>
        <p>QSI • Literature Review • Intensive Care</p>
        <p>-----</p>
        <p>A review of the applications of QSI use to combat antimicrobial resistant strains of Pseudomonas aeruginosa in intensive care settings.</p>
      </div>

      <div class="carousel-card" data-link="/Projects/Bioinformatics_CC">
        <h3>Bioinformatics Crash Course</h3>
        <p>Bioinformatics • Data Science • Python</p>
        <p>-----</p>
        <p>A little project refreshing my knowledge of Python and gaining experience using it in a bioinformatics setting - aided by the use of CoPilot LLM.</p>
      </div>

    </div>
  </div>
</div>

</div> <!-- end main-content -->

<script>
window.addEventListener("load", () => {
  setTimeout(() => {
    document.getElementById("loader").classList.add("fade-out");
  }, 5000);
});

const track = document.querySelector('.carousel-track');
const cards = Array.from(document.querySelectorAll('.carousel-card'));

let currentIndex = 0;
let cardWidth;

function recalc() {
  cardWidth = cards[0].offsetWidth + 32;
  updateCarousel();
}

window.addEventListener('resize', recalc);
setTimeout(recalc, 50);

function updateCarousel() {
  track.style.transform = `translateX(calc(50% - ${(currentIndex + 0.5) * cardWidth}px))`;

  cards.forEach((card, i) => {
    card.classList.toggle('active', i === currentIndex);
  });
}

function moveTo(index) {
  const maxIndex = cards.length - 1;
  currentIndex = Math.max(0, Math.min(index, maxIndex));
  updateCarousel();
}

cards.forEach((card, index) => {
  card.addEventListener('click', () => {
    if (index === currentIndex) {
      window.location = card.dataset.link;
    } else {
      moveTo(index);
    }
  });
});

// Swipe support
let startX = 0;

track.addEventListener('touchstart', e => {
  startX = e.touches[0].clientX;
});

track.addEventListener('touchend', e => {
  const diff = e.changedTouches[0].clientX - startX;

  if (diff > 50) moveTo(currentIndex - 1);
  if (diff < -50) moveTo(currentIndex + 1);
});
</script>

---
layout: default
---
<style>
.carousel-container {
  width: 100%;
  overflow: hidden;
  margin: 3rem auto;
  padding: 4rem 0; /* ensures rounded corners are visible */
  position: relative;
}

/* Fade-out edges */
.carousel-container::before,
.carousel-container::after {
  content: "";
  position: absolute;
  top: 0;
  width: 180px; /* wider fade for smoother look */
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
  min-width: 400px;
  height: 400px;
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

.carousel-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>

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
        <p>A Genome Wide Association Study using Mendelian randomisation with infectious disease as an outcome as part of the MRC-IEU.</p>
      </div>

      <div class="carousel-card" data-link="/Projects/Communication">
        <h3>From superbugs to scapegoats: Could antimicrobial resistance misinformation fuel xenophobic discourse?</h3>
        <p>Public Health • Scientific Communication • AMR</p>
        <p>-----</p>
        <p>A commentary piece warning of a foreseeable risk of AMR communication being manipulated and used to disseminate xenophobic rhetoric and detailing the role medical scientists have to play in combating misinformation and preserving public understanding.</p>
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

<script>
const track = document.querySelector('.carousel-track');
const cards = Array.from(document.querySelectorAll('.carousel-card'));

let currentIndex = 0;
let cardWidth;

function recalc() {
  cardWidth = cards[0].offsetWidth + 32; // width + gap
  updateCarousel();
}

window.addEventListener('resize', recalc);
setTimeout(recalc, 50); // allow layout to settle

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

// Click to centre
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




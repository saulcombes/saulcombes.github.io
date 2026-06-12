---
layout: default
---

<style>
.carousel-container {
  width: 100%;
  overflow: hidden;
  margin: 3rem auto;
}

.carousel-track {
  display: flex;
  height: 420
  gap: 2rem;
  transition: transform 0.6s ease;
  will-change: transform;
}

.carousel-card {
  min-width: 340px;
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

      <div class="carousel-card" data-link="/projects/plate-imager">
        <h3>Plate Handling & Imaging</h3>
        <p>Automation • Engineering • Image Analysis</p>
      </div>

      <div class="carousel-card" data-link="/projects/phea">
        <h3>PHEA ICU Microbiology</h3>
        <p>Clinical Data • Infection • Aspiration</p>
      </div>

      <div class="carousel-card" data-link="/projects/osint">
        <h3>OSINT & Health Misinformation</h3>
        <p>Digital Health • Narrative Analysis</p>
      </div>

      <div class="carousel-card" data-link="/projects/ntc">
        <h3>NTC Variant Calling Course</h3>
        <p>Bioinformatics • Teaching • Pipelines</p>
      </div>

    </div>
  </div>
</div>

<script>
const track = document.querySelector('.carousel-track');
let cards = Array.from(document.querySelectorAll('.carousel-card'));
const cardWidth = cards[0].offsetWidth + 32; // width + gap

// Clone first and last 2 cards for smooth looping
const clonesBefore = cards.slice(-2).map(c => c.cloneNode(true));
const clonesAfter = cards.slice(0, 2).map(c => c.cloneNode(true));

clonesBefore.forEach(c => track.prepend(c));
clonesAfter.forEach(c => track.append(c));

let allCards = Array.from(document.querySelectorAll('.carousel-card'));
let currentIndex = 2; // start on the real first card

function setPosition(animate = true) {
  track.style.transition = animate ? "transform 0.6s ease" : "none";
  track.style.transform = `translateX(calc(50% - ${(currentIndex + 0.5) * cardWidth}px))`;

  allCards.forEach((card, i) => {
    card.classList.toggle('active', i === currentIndex);
  });
}

function moveTo(index) {
  currentIndex = index;
  setPosition(true);
}

track.addEventListener('transitionend', () => {
  // If we hit a clone, jump to the real card without animation
  if (currentIndex === 0) {
    currentIndex = cards.length;
    setPosition(false);
  }
  if (currentIndex === allCards.length - 1) {
    currentIndex = cards.length - 1;
    setPosition(false);
  }
});

// Click to centre
allCards.forEach((card, index) => {
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

// Initial position
setPosition(false);
</script>


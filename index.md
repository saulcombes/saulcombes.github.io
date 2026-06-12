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
  gap: 2rem;
  transition: transform 0.6s ease;
}

.carousel-card {
  min-width: 340px;
  height: 240px;
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

      <div class="carousel-card" data-link="/projects/plate2">
        <h3>Plate Imager v2</h3>
        <p>XY Motion • Autofocus • ML Quantification</p>
      </div>

    </div>
  </div>
</div>
<script>
const track = document.querySelector('.carousel-track');
let cards = Array.from(document.querySelectorAll('.carousel-card'));
let currentIndex = 2; // start in the middle

function updateCarousel() {
  const cardWidth = cards[0].offsetWidth + 32; // width + gap
  track.style.transform = `translateX(calc(50% - ${(currentIndex + 0.5) * cardWidth}px))`;

  cards.forEach((card, i) => {
    card.classList.toggle('active', i === currentIndex);
  });
}

function loopCarousel() {
  if (currentIndex <= 0) {
    const last = cards.pop();
    cards.unshift(last);
    track.prepend(last);
    currentIndex = 1;
  } else if (currentIndex >= cards.length - 1) {
    const first = cards.shift();
    cards.push(first);
    track.append(first);
    currentIndex = cards.length - 2;
  }
}

cards.forEach((card, index) => {
  card.addEventListener('click', () => {
    if (index === currentIndex) {
      window.location = card.dataset.link;
    } else {
      currentIndex = index;
      loopCarousel();
      updateCarousel();
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

  if (diff > 50) currentIndex--;
  if (diff < -50) currentIndex++;

  loopCarousel();
  updateCarousel();
});

// Initial position
updateCarousel();
</script>

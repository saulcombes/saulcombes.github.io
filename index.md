---
layout: default
---

<style>
.carousel-container {
  width: 100%;
  overflow: hidden;
  margin: 2rem auto;
}

.carousel-track {
  display: flex;
  gap: 1.5rem;
  transition: transform 0.6s ease;
}

.carousel-card {
  min-width: 260px;
  height: 180px;
  padding: 1rem;
  border-radius: 18px;
  backdrop-filter: blur(12px);
  background: rgba(255, 255, 255, 0.25);
  border: 1px solid rgba(255, 255, 255, 0.35);
  box-shadow: 0 8px 25px rgba(0,0,0,0.15);
  cursor: pointer;
  transition: transform 0.4s ease, opacity 0.4s ease;
  opacity: 0.5;
}

.carousel-card.active {
  transform: scale(1.1);
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
  
## Featured Projects
<h2>Active Projects</h2>

<div class="carousel-container">
  <div class="carousel-wrapper">
    <div class="carousel-track">

      <div class="carousel-card active" data-link="/projects/plate-imager">
        <h3>Plate Handling & Imaging</h3>
        <p>Automation • Engineering</p>
      </div>

      <div class="carousel-card" data-link="/projects/phea">
        <h3>PHEA ICU Microbiology</h3>
        <p>Clinical Data • Infection</p>
      </div>

      <div class="carousel-card" data-link="/projects/osint">
        <h3>OSINT & Health Misinformation</h3>
        <p>Digital Health • Narratives</p>
      </div>

    </div>
  </div>
</div>

<script>
const track = document.querySelector('.carousel-track');
const cards = Array.from(document.querySelectorAll('.carousel-card'));
let currentIndex = 0;

function updateCarousel() {
  const cardWidth = cards[0].offsetWidth + 24; // width + gap
  track.style.transform = `translateX(calc(50% - ${(currentIndex + 0.5) * cardWidth}px))`;

  cards.forEach((card, i) => {
    card.classList.toggle('active', i === currentIndex);
  });
}

cards.forEach((card, index) => {
  card.addEventListener('click', () => {
    if (index === currentIndex) {
      window.location = card.dataset.link;
    } else {
      currentIndex = index;
      updateCarousel();
    }
  });
});

// Touch/swipe support
let startX = 0;

track.addEventListener('touchstart', e => {
  startX = e.touches[0].clientX;
});

track.addEventListener('touchend', e => {
  const endX = e.changedTouches[0].clientX;
  const diff = endX - startX;

  if (diff > 50 && currentIndex > 0) {
    currentIndex--;
  } else if (diff < -50 && currentIndex < cards.length - 1) {
    currentIndex++;
  }

  updateCarousel();
});

// Initial positioning
updateCarousel();
</script>

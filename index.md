---
layout: default
---

<div id="loader">
  <img src="/assets/img/bacteria.png" alt="loading icon" class="loader-icon">
</div>

<!-- FULL-WIDTH PETRI DISH NAVIGATION -->
<style>
/* Full-width centred section */
.petri-section {
  width: 100%;
  display: flex;
  justify-content: center;
  margin: 4rem 0 5rem 0;
}

/* Responsive Petri dish container */
.petri-nav {
  width: min(480px, 80vw);
  height: min(480px, 80vw);
  position: relative;
}

/* Petri dish base image */
.petri-dish {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  object-fit: cover;
  position: absolute;
  inset: 0;
  z-index: 1;
}

/* Colony wrapper (clickable) */
.petri-colony {
  position: absolute;
  width: 90px;   /* colony size */
  height: 90px;
  cursor: pointer;
  transition: 0.25s ease;
  z-index: 3;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Colony image (NO overlay) */
.colony-img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  border-radius: 50%;
  position: relative;
  z-index: 3;
  transition: 0.25s ease;
}

/* Hover glow */
.petri-colony:hover .colony-img {
  transform: scale(1.18);
  filter: brightness(1.2);
}

/* Labels */
.petri-colony::after {
  content: attr(data-label);
  position: absolute;
  left: 50%;
  top: -26px;
  transform: translateX(-50%);
  background: white;
  padding: 4px 8px;
  border-radius: 6px;
  font-size: 0.8rem;
  opacity: 0;
  pointer-events: none;
  transition: 0.25s ease;
  border: 1px solid rgba(0,0,0,0.1);
  z-index: 10;
}

.petri-colony:hover::after {
  opacity: 1;
}

/* Colony positions (moved inward) */
.colony-home      { top: 18%; left: 50%; transform: translateX(-50%); }
.colony-projects  { top: 50%; left: 82%; transform: translateY(-50%); }
.colony-research  { top: 82%; left: 50%; transform: translateX(-50%); }
.colony-skills    { top: 50%; left: 18%; transform: translateY(-50%); }
</style>

# Saul Combes  
### Cellular and Molecular Medicine MSc

I integrate Mechanistic Biology, Clinical Data, and Computational Methods to understand infection and injury.

<div class="main-content">

<!-- PETRI DISH NAVIGATION SECTION -->
<div class="petri-section">
  <div class="petri-nav">

    <!-- Petri Dish Base -->

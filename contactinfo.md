---
layout: page
title: "Let’s Connect!"
subtitle: 🫱✨🫲
permalink: /contactinfo/
---

<!-- Font Awesome for icons ONLY on this page -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

<style>
  #contact-buttons {
    font-family: 'Open Sans', 'Helvetica Neue', Helvetica, Arial, sans-serif;
  }

  #contact-buttons .contact-intro {
    font-size: 1.2rem;
    font-weight: 500;
    margin-bottom: 20px;
  }

  #contact-buttons .button-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0;
  }

  #contact-buttons .contact-button {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
    padding: 18px;
    font-size: 18px;
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: white !important;
    border: none;
    text-decoration: none;
    border-radius: 0; /* no rounding by default */
    transition: all 0.3s ease;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
  }

  #contact-buttons .button-grid:hover .contact-button {
    opacity: 0.5;
  }

  #contact-buttons .contact-button:hover {
    transform: scale(1.08);
    opacity: 1 !important;
    border-radius: 8px; /* rounding only on hover */
    z-index: 2;
  }

  #contact-buttons .contact-button i,
  #contact-buttons .contact-button img {
    width: 22px;
    height: 22px;
  }

  #contact-buttons .contact-button img {
    object-fit: contain;
    filter: brightness(0) invert(1);
    transition: filter 0.3s ease;
  }

  #contact-buttons .contact-button:hover img {
    filter: none;
  }

  /* Platform Colors */
  #contact-buttons .linkedin   { background-color: #0077b5; }
  #contact-buttons .github     { background-color: #333; }
  #contact-buttons .email      { background-color: #d44638; }
  #contact-buttons .whatsapp   { background-color: #25D366; }
  #contact-buttons .resume     { background-color: #6c63ff; }
  #contact-buttons .portfolio  { background-color: #003366; }
  #contact-buttons .facebook   { background-color: #1877f2; }
  #contact-buttons .instagram  { background-color: #e1306c; }
  #contact-buttons .x-twitter  { background-color: #000000; }
  #contact-buttons .about      { background-color: #444444; }

  #contact-buttons .disclaimer {
    margin-top: 20px;
    font-size: 0.9rem;
    font-style: italic;
    color: gray;
  }
</style>

<div id="contact-buttons">

  <div class="contact-intro">
    🔴 Hi! This is <strong>Cryza</strong>, Ekram's personal AI* assistant. How can I help you connect with Ekram?
  </div>

  <div class="button-grid">

    <a href="https://www.linkedin.com/in/ekram-ullah-ahmed/" class="contact-button linkedin" target="_blank">
      <i class="fab fa-linkedin"></i> LinkedIn
    </a>

    <a href="https://github.com/Ekram49" class="contact-button github" target="_blank">
      <i class="fab fa-github"></i> GitHub
    </a>

    <a href="mailto:ekramullahzaki@gmail.com" class="contact-button email">
      <i class="fas fa-envelope"></i> Email
    </a>

    <a href="https://wa.me/19294599555" class="contact-button whatsapp" target="_blank">
      <i class="fab fa-whatsapp"></i> WhatsApp
    </a>

    <a href="https://drive.google.com/file/d/1HnU5TD-siw7CX4ezt4imaF2FTCv6M6pR/view?usp=sharing" class="contact-button resume" target="_blank">
      <img src="/assets/icons/resume-icon.png" alt="Resume Icon"> Resume
    </a>

    <a href="https://ekram49.github.io/" class="contact-button portfolio" target="_blank">
      <img src="/assets/icons/portfolio-icon.png" alt="Portfolio Icon"> Portfolio
    </a>

    <a href="https://www.facebook.com/ekram.zaki" class="contact-button facebook" target="_blank">
      <i class="fab fa-facebook-f"></i> Facebook
    </a>

    <a href="https://www.instagram.com/" class="contact-button instagram" target="_blank">
      <i class="fab fa-instagram"></i> Instagram
    </a>

    <a href="https://x.com/EkramAh56552843" class="contact-button x-twitter" target="_blank">
      <i class="fab fa-x-twitter"></i> X (Twitter)
    </a>

    <a href="https://ekram49.github.io/aboutme/" class="contact-button about" target="_blank">
      <i class="fas fa-user"></i> About Ekram
    </a>

  </div>

  <div class="disclaimer">
    *No actual AI was harmed (or used) in the making of this assistant. But hey, everyone’s claiming to use AI these days 🤫🤖
  </div>

</div>

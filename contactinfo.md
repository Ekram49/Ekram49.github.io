---
layout: page
title: "Let’s Connect"
permalink: /contactinfo/
---

<style>
  .contact-intro {
    font-size: 1.2rem;
    font-weight: 500;
    margin-bottom: 20px;
  }

  .button-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0px;
  }

  .contact-button {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
    padding: 18px;
    font-size: 1.1rem;
    font-weight: 600;
    color: white;
    border: 1px solid #ccc;
    text-decoration: none;
    transition: transform 0.2s ease;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
  }

  .contact-button:hover {
    transform: scale(1.05);
    z-index: 2;
    color: white !important; /* Override global link hover color */
  }

  .contact-button i,
  .contact-button img {
    width: 22px;
    height: 22px;
  }

  .contact-button img {
    object-fit: contain;
    border-radius: 4px;
  }

  /* Platform Colors */
  .linkedin   { background-color: #0077b5; }
  .github     { background-color: #333; }
  .email      { background-color: #d44638; }
  .whatsapp   { background-color: #25D366; }
  .resume     { background-color: #6c63ff; }
  .portfolio  { background-color: #003366; }
  .facebook   { background-color: #1877f2; }
  .instagram  { background-color: #e1306c; }
  .x-twitter  { background-color: #000000; }
  .about      { background-color: #444444; }

  .disclaimer {
    margin-top: 20px;
    font-size: 0.9rem;
    font-style: italic;
    color: gray;
  }
</style>

<div class="contact-intro">
  👋 Hi! This is <strong>Jarvis</strong>, Ekram's personal AI* assistant. How can I help you connect with Ekram?
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
    <img src="https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/My%20Headshot.png" alt="Resume Icon"> Resume
  </a>

  <a href="https://ekram49.github.io/" class="contact-button portfolio" target="_blank">
    <img src="https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/My%20Headshot.png" alt="Portfolio Icon"> Portfolio
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
  *Test
</div>

<!-- Load Font Awesome -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

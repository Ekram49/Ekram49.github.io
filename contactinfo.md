---
layout: page
title: "Let’s Connect!"
subtitle: 🫱✨🫲
permalink: /contactinfo/
---

<!-- Font Awesome (only used in this section) -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

<style>
  /* Bigger italic intro line, like Jekyll subtitle */
  .contact-intro {
    font-family: 'Open Sans', 'Helvetica Neue', Helvetica, Arial, sans-serif;
    font-size: 2rem;
    font-style: italic;
    font-weight: 400;
    margin-bottom: 20px;
    text-align: center;
    line-height: 1.2;
  }

  .button-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0;
    max-width: 800px;
    margin: 0 auto;
    padding: 0 10px;
  }

  @media (max-width: 600px) {
    .button-grid {
      grid-template-columns: 1fr;
    }
  }

  .contact-button {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 14px;
    padding: 18px;
    font-family: 'Open Sans', 'Helvetica Neue', Helvetica, Arial, sans-serif;
    font-size: 18px;
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: white !important;
    border: none;
    text-decoration: none;
    border-radius: 0;
    transition: all 0.3s ease;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
    width: 100%;
    box-sizing: border-box;
  }

  /* Dim all buttons on grid hover except hovered */
  .button-grid:hover .contact-button {
    opacity: 0.5;
  }
  .contact-button:hover {
    transform: scale(1.08);
    opacity: 1 !important;
    border-radius: 8px;
    z-index: 2;
  }

  /* Icon styles */
  .contact-button i,
  .contact-button img {
    width: 26px;
    height: 26px;
    line-height: 26px;
    filter: brightness(0) invert(1);
    box-shadow: 0 1px 3px rgba(0,0,0,0.3);
    transition: filter 0.3s ease, box-shadow 0.3s ease;
  }

  .contact-button img {
    object-fit: contain;
  }

  /* Remove filter on hover so color icons show */
  .contact-button:hover i,
  .contact-button:hover img {
    filter: none;
    box-shadow: 0 2px 6px rgba(0,0,0,0.45);
  }

  /* Align text baseline with icons */
  .contact-button span {
    display: inline-flex;
    align-items: center;
    line-height: 1;
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
    margin-top: 30px;
    font-size: 0.9rem;
    font-style: italic;
    color: gray;
    text-align: center;
  }
</style>

<div class="contact-intro">
  🔴 Hi! This is <strong>Cryza</strong>, Ekram's personal AI* assistant. How can I help you connect with Ekram?
</div>

<div class="button-grid">

  <a href="https://www.linkedin.com/in/ekram-ullah-ahmed/" class="contact-button linkedin" target="_blank">
    <i class="fab fa-linkedin"></i><span>LinkedIn</span>
  </a>

  <a href="https://github.com/Ekram49" class="contact-button github" target="_blank">
    <i class="fab fa-github"></i><span>GitHub</span>
  </a>

  <a href="mailto:ekramullahzaki@gmail.com" class="contact-button email">
    <i class="fas fa-envelope"></i><span>Email</span>
  </a>

  <a href="https://wa.me/19294599555" class="contact-button whatsapp" target="_blank">
    <i class="fab fa-whatsapp"></i><span>WhatsApp</span>
  </a>

  <a href="https://drive.google.com/file/d/1HnU5TD-siw7CX4ezt4imaF2FTCv6M6pR/view?usp=sharing" class="contact-button resume" target="_blank">
    <img src="/assets/icons/resume-icon.png" alt="Resume Icon"><span>Resume</span>
  </a>

  <a href="https://ekram49.github.io/" class="contact-button portfolio" target="_blank">
    <img src="/assets/icons/portfolio-icon.png" alt="Portfolio Icon"><span>Portfolio</span>
  </a>

  <a href="https://www.facebook.com/ekram.zaki" class="contact-button facebook" target="_blank">
    <i class="fab fa-facebook-f"></i><span>Facebook</span>
  </a>

  <a href="https://www.instagram.com/" class="contact-button instagram" target="_blank">
    <i class="fab fa-instagram"></i><span>Instagram</span>
  </a>

  <a href="https://x.com/EkramAh56552843" class="contact-button x-twitter" target="_blank">
    <i class="fab fa-x-twitter"></i><span>X (Twitter)</span>
  </a>

  <a href="https://ekram49.github.io/aboutme/" class="contact-button about" target="_blank">
    <i class="fas fa-user"></i><span>About Ekram</span>
  </a>

</div>

<div class="disclaimer">
  *No actual AI was harmed (or used) in the making of this assistant. But hey, everyone’s claiming to use AI these days 🤫🤖
</div>

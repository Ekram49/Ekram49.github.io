---
layout: page
title: "Let’s Connect!"
subtitle: 🫱✨🫲
permalink: /contactinfo/
---

<!-- Font Awesome (only used in button section) -->
<div id="fa-contact-scope">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
</div>

<style>
  .contact-intro {
    font-size: 1.6rem;
    font-style: italic;
    font-family: 'Open Sans', 'Helvetica Neue', Helvetica, Arial, sans-serif;
    text-align: center;
    margin-bottom: 20px;
  }

  .button-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 15px;
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
    gap: 12px;
    padding: 16px 22px;
    font-family: 'Open Sans', 'Helvetica Neue', Helvetica, Arial, sans-serif;
    font-weight: 700;
    font-size: 18px;
    text-transform: uppercase;
    letter-spacing: 1.2px;
    color: white !important;
    border: 2.5px solid transparent;
    border-radius: 12px;
    background: linear-gradient(145deg, #005582, #0077b5); /* fallback color, overridden by platform classes */
    box-shadow:
      0 4px 6px rgba(0,0,0,0.15),
      inset 0 -3px 5px rgba(255,255,255,0.2);
    cursor: pointer;
    transition: 
      transform 0.25s cubic-bezier(.4,0,.2,1),
      box-shadow 0.3s ease,
      background 0.3s ease,
      border-color 0.3s ease;
    width: 100%;
    box-sizing: border-box;
    text-decoration: none;
  }

  .contact-button i {
    font-size: 22px;
    filter: drop-shadow(0 1px 1px rgba(0,0,0,0.2));
  }

  /* Remove old grid hover opacity */
  .button-grid:hover .contact-button {
    opacity: 1 !important;
  }

  .contact-button:hover,
  .contact-button:focus {
    transform: translateY(-3px) scale(1.05);
    box-shadow:
      0 8px 15px rgba(0,0,0,0.3),
      inset 0 -3px 8px rgba(255,255,255,0.3);
    border-color: rgba(255,255,255,0.6);
    text-decoration: none;
    outline: none;
  }

  /* Platform color gradients and border colors */
  .linkedin {
    background: linear-gradient(145deg, #005582, #0077b5);
    border-color: #004466;
  }

  .github {
    background: linear-gradient(145deg, #222, #444);
    border-color: #111;
  }

  .email {
    background: linear-gradient(145deg, #b5392f, #d44638);
    border-color: #8b2d24;
  }

  .whatsapp {
    background: linear-gradient(145deg, #1ebd56, #25D366);
    border-color: #198c40;
  }

  .resume {
    background: linear-gradient(145deg, #594de8, #6c63ff);
    border-color: #4a3ecf;
  }

  .portfolio {
    background: linear-gradient(145deg, #002244, #003366);
    border-color: #001a33;
  }

  .facebook {
    background: linear-gradient(145deg, #0f62c7, #1877f2);
    border-color: #0b4b9a;
  }

  .instagram {
    background: linear-gradient(145deg, #b73661, #e1306c);
    border-color: #8c274a;
  }

  .x-twitter {
    background: linear-gradient(145deg, #111, #000000);
    border-color: #222;
  }

  .about {
    background: linear-gradient(145deg, #444, #666);
    border-color: #333;
  }

  .disclaimer {
    margin-top: 30px;
    font-size: 0.9rem;
    font-style: italic;
    color: gray;
    text-align: center;
  }

  /* Resume dropdown styles */
  .resume-dropdown {
    position: relative;
    width: 100%;
  }

  .resume-dropdown .contact-button {
    width: 100%;
  }

  .resume-dropdown-content {
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    flex-direction: column;
    background: #594de8;
    border-radius: 0 0 12px 12px;
    overflow: hidden;
    z-index: 1000;
  }

  .resume-dropdown:hover .resume-dropdown-content {
    display: flex;
  }

  .resume-dropdown-content a {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding: 14px 20px;
    font-family: 'Open Sans', 'Helvetica Neue', Helvetica, Arial, sans-serif;
    font-weight: 600;
    font-size: 16px;
    color: white !important;
    text-transform: uppercase;
    letter-spacing: 1px;
    background: linear-gradient(145deg, #594de8, #6c63ff);
    border-top: 1px solid rgba(255,255,255,0.2);
    text-decoration: none;
    transition: background 0.3s ease, transform 0.2s ease;
  }

  .resume-dropdown-content a:hover {
    background: linear-gradient(145deg, #483ed2, #5952f5);
    transform: scale(1.03);
  }
</style>

<div class="contact-intro">
  🔴 Hi! This is <strong>Cryza</strong>, Ekram's personal <strong>AI*</strong> assistant. How can I help you connect with Ekram?
</div>

<div class="button-grid">

  <a href="https://www.linkedin.com/in/ekram-ullah-ahmed/" class="contact-button linkedin" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-linkedin"></i> LinkedIn
  </a>

  <a href="https://github.com/Ekram49" class="contact-button github" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-github"></i> GitHub
  </a>

  <a href="mailto:ekramullahzaki@gmail.com" class="contact-button email">
    <i class="fas fa-envelope"></i> Email
  </a>

  <a href="https://wa.me/19294599555" class="contact-button whatsapp" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-whatsapp"></i> WhatsApp
  </a>

  <!-- Resume dropdown -->
  <div class="resume-dropdown">
    <a href="#" class="contact-button resume">
      <i class="fas fa-file-alt"></i> Resume
    </a>
    <div class="resume-dropdown-content">
      <a href="https://drive.google.com/file/d/1HnU5TD-siw7CX4ezt4imaF2FTCv6M6pR/view?usp=sharing" target="_blank" rel="noopener noreferrer">
        <i class="fas fa-database"></i> Data Analyst Resume
      </a>
      <a href="https://drive.google.com/file/d/1JYqaB26nayFT5bfprRoiOq_jn5MVklvY/view?usp=sharing" target="_blank" rel="noopener noreferrer">
        <i class="fas fa-ship"></i> Marine Engineer Resume
      </a>
    </div>
  </div>

  <a href="https://ekram49.github.io/" class="contact-button portfolio" target="_blank" rel="noopener noreferrer">
    <i class="fas fa-book"></i> Portfolio
  </a>

  <a href="https://www.facebook.com/ekram.zaki" class="contact-button facebook" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-facebook-f"></i> Facebook
  </a>

  <a href="https://www.instagram.com/" class="contact-button instagram" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-instagram"></i> Instagram
  </a>

  <a href="https://x.com/EkramAh56552843" class="contact-button x-twitter" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-x-twitter"></i> X (Twitter)
  </a>

  <a href="https://ekram49.github.io/aboutme/" class="contact-button about" target="_blank" rel="noopener noreferrer">
    <i class="fas fa-user"></i> About Ekram
  </a>

</div>

<div class="disclaimer">
  *No actual AI was harmed (or used) in the making of this assistant. But hey, everyone’s claiming to use AI these days 🤫🤖
</div>


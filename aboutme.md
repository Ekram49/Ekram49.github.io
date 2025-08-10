---
layout: page
title: Ekram Ahmed 
subtitle: Maritime Data Analyst
---

<!-- Font Awesome -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />

<style>
  .button-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 16px;
    margin: 30px 0;
  }
  .link-button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding: 14px 24px;
    min-width: 160px;
    height: 46px;
    font: 700 16px 'Open Sans', sans-serif;
    text-transform: uppercase;
    letter-spacing: 1.1px;
    color: white;
    border-radius: 12px;
    border: 2.5px solid transparent;
    cursor: pointer;
    text-decoration: none;
    box-shadow: 0 4px 6px rgba(0,0,0,0.15), inset 0 -3px 5px rgba(255,255,255,0.2);
    transition: all 0.3s ease;
  }
  .link-button:hover,
  .link-button:focus {
    transform: translateY(-3px) scale(1.05);
    box-shadow: 0 8px 15px rgba(0,0,0,0.3), inset 0 -3px 8px rgba(255,255,255,0.3);
    border-color: rgba(255,255,255,0.6);
    outline: none;
  }
  .link-button i { font-size: 20px; }
  .link-portfolio { background: linear-gradient(145deg, #002244, #003366); border-color: #001a33; }
  .link-resume    { background: linear-gradient(145deg, #594de8, #6c63ff); border-color: #4a3ecf; }
  .link-linkedin  { background: linear-gradient(145deg, #005582, #0077b5); border-color: #004466; }
  .link-email     { background: linear-gradient(145deg, #b5392f, #d44638); border-color: #8b2d24; }

  .image-slider {
    position: relative;
    width: 100%;
    max-width: 1000px;
    height: 400px;
    margin: 40px auto;
    overflow: hidden;
    background: transparent;
    border-radius: 12px;
  }

  .slider-track {
    display: flex;
    width: 100%;
    height: 100%;
    transition: transform 0.6s ease;
  }

  .slider-track img {
    flex-shrink: 0;
    width: 100%;
    height: 100%;
    object-fit: contain;
    cursor: zoom-in;
  }

  .arrow {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(0, 0, 0, 0.6);
    color: white;
    padding: 15px;
    font-size: 25px;
    border-radius: 50%;
    cursor: pointer;
    z-index: 10;
    transition: transform 0.2s ease;
    user-select: none;
  }
  .arrow:hover { transform: translateY(-50%) scale(1.2); }
  .arrow-left { left: 10px; }
  .arrow-right { right: 10px; }

  .slider-dots {
    position: absolute;
    bottom: 10px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 10px;
    z-index: 10;
  }
  .slider-dots span {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background: rgba(255,255,255,0.6);
    cursor: pointer;
  }
  .slider-dots span.active { background: white; }

  /* Fullscreen Modal styles */
  #image-modal {
    display: none;
    position: fixed;
    top:0; left:0;
    width: 100vw; height: 100vh;
    background-color: rgba(0,0,0,0.8);
    z-index: 9999;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  #modal-image {
    max-width: 90%;
    max-height: 90%;
  }
  #close-modal {
    position: absolute;
    top: 30px;
    right: 40px;
    font-size: 40px;
    color: white;
    cursor: pointer;
    user-select: none;
  }
</style>

<div class="button-container">
  <a href="https://ekram49.github.io/" class="link-button link-portfolio" target="_blank"><i class="fas fa-book"></i> Portfolio</a>
  <a href="https://drive.google.com/file/d/1HnU5TD-siw7CX4ezt4imaF2FTCv6M6pR/view" class="link-button link-resume" target="_blank"><i class="fas fa-file-alt"></i> Resume</a>
  <a href="https://www.linkedin.com/in/ekram-ullah-ahmed/" class="link-button link-linkedin" target="_blank"><i class="fab fa-linkedin"></i> LinkedIn</a>
  <a href="mailto:ekramullahzaki@gmail.com" class="link-button link-email"><i class="fas fa-envelope"></i> Email</a>
</div>

<!-- Fullscreen Modal -->
<div id="image-modal" style="display: none; position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; background-color: rgba(0,0,0,0.8); z-index: 9999; justify-content: center; align-items: center;">
  <img id="modal-image" src="" alt="Full Image" style="max-width: 90%; max-height: 90%;">
  <span id="close-modal" style="position: absolute; top: 30px; right: 40px; font-size: 40px; color: white; cursor: pointer;">&times;</span>
</div>

<script>
  function initSliders() {
    const sliders = document.querySelectorAll(".image-slider");

    if (sliders.length === 0) {
      // Retry shortly if sliders not yet in DOM
      return setTimeout(initSliders, 100);
    }

    sliders.forEach(slider => {
      const images = JSON.parse(slider.dataset.images || "[]");
      if (images.length === 0) return;

      let currentIndex = 0;
      let autoSlideInterval;

      slider.innerHTML = `
        <div class="arrow arrow-left">&#10094;</div>
        <div class="arrow arrow-right">&#10095;</div>
        <div class="slider-track"></div>
        <div class="slider-dots"></div>
      `;

      const track = slider.querySelector(".slider-track");
      const dotsContainer = slider.querySelector(".slider-dots");
      const leftArrow = slider.querySelector(".arrow-left");
      const rightArrow = slider.querySelector(".arrow-right");

      // Add all images inside track
      images.forEach(src => {
        const img = document.createElement("img");
        img.src = src;
        img.alt = "Slider Image";
        img.addEventListener("click", () => {
          document.getElementById("modal-image").src = src;
          document.getElementById("image-modal").style.display = "flex";
        });
        track.appendChild(img);
      });

      // Create dots
      function updateDots() {
        dotsContainer.innerHTML = "";
        images.forEach((_, i) => {
          const dot = document.createElement("span");
          dot.className = i === currentIndex ? "active" : "";
          dot.addEventListener("click", () => {
            currentIndex = i;
            updateSlider();
            resetAutoSlide();
          });
          dotsContainer.appendChild(dot);
        });
      }

      // Update slider position
      function updateSlider() {
        const offset = -currentIndex * 100;
        track.style.transform = `translateX(${offset}%)`;
        updateDots();
      }

      function nextSlide() {
        currentIndex = (currentIndex + 1) % images.length;
        updateSlider();
      }

      function prevSlide() {
        currentIndex = (currentIndex - 1 + images.length) % images.length;
        updateSlider();
      }

      leftArrow.addEventListener("click", () => {
        prevSlide();
        resetAutoSlide();
      });

      rightArrow.addEventListener("click", () => {
        nextSlide();
        resetAutoSlide();
      });

      // Auto slide every 10 seconds
      function resetAutoSlide() {
        if (autoSlideInterval) clearInterval(autoSlideInterval);
        autoSlideInterval = setInterval(() => {
          nextSlide();
        }, 10000);
      }

      // Pause on hover
      slider.addEventListener("mouseenter", () => {
        if (autoSlideInterval) clearInterval(autoSlideInterval);
      });

      slider.addEventListener("mouseleave", () => {
        resetAutoSlide();
      });

      updateSlider();
      resetAutoSlide();
    });
  }

  // Initialize sliders on DOM ready
  document.addEventListener("DOMContentLoaded", initSliders);

  // Modal logic (close on click X or ESC)
  document.addEventListener("DOMContentLoaded", () => {
    const modal = document.getElementById("image-modal");
    const closeBtn = document.getElementById("close-modal");

    closeBtn.addEventListener("click", () => {
      modal.style.display = "none";
    });

    document.addEventListener("keydown", (e) => {
      if (e.key === "Escape") {
        modal.style.display = "none";
      }
    });
  });
</script>

<!-- Your original content below (unchanged) -->

Hey, this is Ekram—a maritime data analyst with a background that spans marine engineering, pharmaceutical retail, maritime tech startups, and a lot of time spent diving deep into data. 
The sea has shaped a big part of who I am—both in work and in life. If you're curious how someone goes from engine rooms to code, from ports to platforms, stick around. Here's a bit of my journey.

<h2> Early Life </h2>

I was born on a naval base in Khulna, Bangladesh. With my father serving as a naval officer in the Bangladesh Navy, I spent my early years moving from one naval base to another. Growing up in that world gave me rare access to Navy ships, training centers, and the everyday life of sailors. While living on bases, I got to swim, dive, and ride boats with sailors and officers who felt more like family than figures in uniform. Being surrounded by the discipline, camaraderie, and quiet strength of the Navy shaped the way I saw the world—and left me with a deep longing to carve out my own path connected to the sea.

<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Early%20Life/Early%20Life%20-%20Fun.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Early%20Life/Early%20Life%20-%20Navy.png"
  ]'>
</div>

<h2> Academy Life </h2>

My journey as a maritime professional began in 2013 when I joined the prestigious [Bangladesh Marine Academy](http://www.macademy.gov.bd/) as a marine engineering cadet. Over the course of two intense years of pre-sea training, I was introduced to the fundamentals of seamanship, personal survival techniques, fire prevention, marine safety, ship construction, and maritime regulations. As an engineering cadet, I also delved deep into subjects like thermodynamics, marine propulsion systems, electrical and control systems, and the inner workings of shipboard machinery.

I had the privilege of learning from seasoned mariners—Captains and Chief Engineers whose stories stretched across oceans and decades. Their mentorship was as impactful as the textbooks. And equally unforgettable were my coursemates: some of the hardest-working, brilliant, and driven individuals I’ve ever met. Many now serve as officers on ships around the world, work in shore-based maritime roles, or thrive in other industries, bringing the same grit and excellence wherever they go.

<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Academy%20Life/Academy%20-%20Me.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Academy%20Life/Academy%20-%20Group.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Academy%20Life/Academy%20-Swimming.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Academy%20Life/Academy%20-%20Fun.png"
  ]'>
</div>

Beyond the technical curriculum, the Academy was where I learned the value of discipline, leadership, and resilience—qualities deeply rooted in maritime and regimental life. The daily routine, the drills, the inspections, and the unspoken codes of conduct shaped not just how I worked but who I was becoming.

<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Academy%20Life/Academy%20-%20Passing%20Out%20-%20Group.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Academy%20Life/Academy%20-%20Passing%20Out%20-%20Ceremony.png"
  ]'>
</div>


<h2> Sea Life </h2>

After graduating from the Academy, I began my sea career aboard [Bashundhara 7](https://www.marinetraffic.com/en/ais/details/ships/shipid:735308/mmsi:-8906834/imo:8906834/vessel:BASHUNDHARA_7), a bulk carrier, as a trainee marine engineer. On board, I got hands-on experience with engine room operations—assisting in the maintenance of the main engine, auxiliary engines, boilers, pumps, compressors, and other vital systems. I learned how to keep the heart of the ship running, often under challenging and unpredictable conditions.

Later, I continued my training on [Bashundhara 8](https://www.marinetraffic.com/en/ais/details/ships/shipid:735308/mmsi:-8906834/imo:8906834/vessel:BASHUNDHARA_8), a sister vessel with a similar setup and sailing pattern. Between the two ships, I completed the 13 months of sea time required for cadetship, gaining exposure to a wide range of operations, watchkeeping routines, and safety drills.

Life at sea was as demanding as it was rewarding. I sailed alongside seasoned marine engineers and officers, traveled to foreign ports, and experienced the unique rhythm of life aboard a merchant vessel. I met people from different cultures, adapted to long voyages, and learned to work as part of a close-knit crew in a constantly moving environment.

<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Ship%20Life/Ship%20-%20Uniform.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Ship%20Life/Ship%20-%20Dry%20Dock.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Ship%20Life/Ship%20-%20Shore%20Leave.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Ship%20Life/Ship%20-%20Onboard.png"
  ]'>
</div>

Those months at sea taught me more than just engineering—they taught me discipline, resilience, teamwork, and how to stay calm when things don’t go as planned. The experience shaped my character and laid the foundation for everything that followed in both my personal and professional life.


<h2> Academy Life 2.0</h2>


After completing my sea training, I returned to the Academy for advanced marine engineering courses and certifications. This time, the theory came alive—what once seemed abstract now made perfect sense in the context of my time onboard. Concepts like thermodynamics, electrical systems, and engine room operations felt far more intuitive, and I was able to connect classroom lessons with real-life challenges I’d faced at sea.

It was also a chance to reunite with many of my coursemates. We shared our sea stories, exchanged insights, and learned from each other’s experiences on different vessels across the globe. That exchange enriched my understanding and broadened my perspective of the industry.

<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Academy%20Life%202.0/Academy%202.0%20(1).png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Academy%20Life%202.0/Academy%202.0%20(2).png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Academy%20Life%202.0/Academy%202.0%20(3).png"
  ]'>
</div>

Alongside the coursework, I also completed a thesis on battery energy storage systems (BESS) and their integration with a ship’s power generation system. The research explored how BESS could address the limitations of conventional marine electrical systems—offering smarter power management, reducing auxiliary engine running hours, and delivering both economic and environmental benefits via fuel savings and reduced blackouts. I analyzed control strategies, engine load responses, and system design, and proposed improvements to enhance efficiency and overcome current limitations.

After successfully defending my thesis, I earned my Bachelor’s in Marine Engineering from [Bangladesh Maritime University](https://bmu.edu.bd/) in 2019.


<h2> Tech Life </h2>

After graduation, I moved to the US and decided to pivot my career toward data analytics within the maritime industry. To build the right skill set, I completed courses in data science and analytics, where I gained expertise in statistical analysis, data visualization, SQL, Python, and tools like Tableau and Excel. Beyond the technical skills, I developed critical problem-solving abilities, effective communication, and project management techniques essential for collaborating across teams.

Combining these new skills with my maritime background helped me secure roles at innovative industry leaders in the maritime tech space like [Nautilus Labs](https://www.danelec.com/newsroom/danelec-acquires-nautilus-labs-ai-technology-platform-to-gain-deeper-insights-within-sustainability-and-safety
) and [Sofar Ocean]("https://www.sofarocean.com/"). There, I had the privilege of working alongside some of the most talented, driven, and forward-thinking professionals I’ve ever known—people passionate about solving complex challenges in shipping and climate tech.

My work ranged from data analytics and client communications to developing tools and insights focused on voyage simulation and optimization, vessel performance monitoring, process automation, weather routing, and post-voyage reporting. I regularly collaborated with product and engineering teams—contributing to project planning, prototyping software solutions, and serving as a subject matter expert on maritime operations, shipping logistics, and voyage optimization.

<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Tech%20Life/Tech%20-%20Nautilus%201.jpg",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Tech%20Life/Tech%20-%20Nautilus%202.jpg",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Tech%20Life/Tech%20-%20Sofar.jpg"
  ]'>
</div>

My firsthand experience onboard ships proved invaluable, earning me respect from colleagues who recognized how practical maritime knowledge enhanced our solutions. I also played a key role in hiring and training new and existing team members, sharing my maritime insights to help them better understand the industry and contribute to building practical, effective products and services.


<h2> Geek Life </h2>

Outside of work, I’m pretty obsessed with the ocean—not just from a seafarer’s point of view, but also in terms of marine life and sustainability. I'm also curious about aviation, healthcare tech, and renewable energy (particularly battery innovations). Basically, if it’s data-rich and meaningful, I want to explore it.

<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20Portfolio%20Landing%20Page.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20Portfolio%20Post.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Portfolio%20Contact.png"
  ]'>
</div>

This blog is where I share some of those explorations—data projects, visualizations, and thoughts on topics I care about.

<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20GC%20to%20RL.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20Predicted%20Positions.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20Email%20Map.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20VO%20Map.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20Multi%20Segment%20Map.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20GFW%20Map.png"
  ]'>
</div>

<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20-%20Adherence%202.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20Alignment.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20Max%20TCE.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20Weather%20Forecast.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20Performance.png"
  ]'>
</div>

<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20Prediction%20Table%201.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20Prediction%20Table%202.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20ETA%20Simulation.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20Nautilus%20-%20YTD%20AER.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Geek%20Life/Geek%20-%20GFW%20Features.png"
  ]'>
</div>

<h2> Fun Life </h2>

When I’m not working or geeking out over datasets, you’ll probably find me doing kettlebell workouts, long-distance swimming, or cruising around NYC on my e-bike or electric skateboard. I’m currently working on a few personal goals: getting my scuba certification, private pilot license, and skydiving license—all within this year. Wish me luck!

<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Fun%20Life/Fun%20-%20Swimming.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Fun%20Life/Fun%20-%20Skateboarding.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Fun%20Life/Fun%20-%20Diving.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Fun%20Life/Fun%20-%20Flying.png"
  ]'>
</div>

<h2> Life(!) Life </h2>

This is a tough one! I could probably write a dozen pages about the people in my life—friends, family, well-wishers—who make this life worth living and thriving..... Maybe someday I will!

But for today, I’ll let the pictures do the talking. Here are a few precious moments with them!

### Family
<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Life%20(!)%20Life/Family/Life%20-%20Family%20-%20Childhood.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Life%20(!)%20Life/Family/Life%20-%20Family%20in%20Academy.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Life%20(!)%20Life/Family/Life%20-%20Family%20-%20Adult.png"  
  ]'>
</div>

### Extended Family
<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Life%20(!)%20Life/Cousins/Life%20-%20Cousin%27s%20Wedding.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Life%20(!)%20Life/Cousins/Life%20-%20Sister%27s%20Wedding.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Life%20(!)%20Life/Cousins/Life%20-%20Cousins%20(Father%27s%20Side).png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Life%20(!)%20Life/Cousins/Life%20-%20Cousins%20(Mother%27s%20Side).png"
  ]'>
</div>

### Safa: MY Niece, OUR Joy — the Heartbeat of the Family!
<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Life%20(!)%20Life/Safa/Life%20-%20Safa%20Sleeping.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Life%20(!)%20Life/Safa/Life%20-%20Safa%20Hanging%20On.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Life%20(!)%20Life/Safa/Life%20-%20Safa%20Fun.png"
  ]'>
</div>

### Friends: The Family Outside the Family

<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Life%20(!)%20Life/Friends/Life%20-%20School%20Friends%201.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Life%20(!)%20Life/Friends/Life%20-%20School%20Friends%202.png",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Life%20(!)%20Life/Friends/Life%20-%20Academy%20Friends.png"
  ]'>
</div>

<h2> Let's Connect! </h2>

If anything in my blog catches your interest—or if you just feel like saying hi—I’d love to hear from you! Doesn’t matter who you are or where you are in your journey; if you feel like connecting, you’re more than welcome to. You can always find me on [LinkedIn](https://www.linkedin.com/in/ekram-ullah-ahmed/), or you can just [email me](mailto:ekramullahzaki@gmail.com) —my inbox is always open!

<b>P.S.</b> I started this blog about five years ago, but didn’t pay much attention to it. Until recently, my "About Me" section still had a few lines from the default template claiming there was a movie made about me! Someone read that, got curious, ended up watching the whole movie, and was very confused until I explained it was just placeholder text.......funny, right?

I was going to remove it, but then thought... nah, I’ll just keep it as it is! If you do decide to watch the movie, just know—full disclosure—it has absolutely nothing to do with me! I hadn’t even seen it until I was asked about it......I'm no farm boy, and I definitely don't know any Buttercup! But it’s a good (kinda weird.....but good!) movie—so enjoy!

<!-- Slider container -->
<div class="image-slider" 
  data-images='[
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/P.S./P.S%201.jpg",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/P.S./P.S%202.jpg",
    "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/P.S./P.S%203.jpg"
  ]'>
</div>

### My history

To be honest, I'm having some trouble remembering right now, so why don't you just watch [my movie](http://en.wikipedia.org/wiki/The_Princess_Bride_%28film%29) and it will answer **all** your questions.

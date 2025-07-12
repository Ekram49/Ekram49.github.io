---
layout: page
title: Ekram Ahmed 
subtitle: Maritime Data Analyst
---

<!-- Font Awesome for icons -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />

<style>
  /* Buttons container to center and space them */
  .button-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 16px;
    margin: 30px 0;
  }

  /* Modern 3D button style */
  .link-button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding: 14px 24px;
    min-width: 160px;
    height: 46px;
    font-family: 'Open Sans', 'Helvetica Neue', Helvetica, Arial, sans-serif;
    font-weight: 700;
    font-size: 16px;
    text-transform: uppercase;
    letter-spacing: 1.1px;
    color: white;
    border-radius: 12px;
    border: 2.5px solid transparent;
    cursor: pointer;
    text-decoration: none;
    box-shadow:
      0 4px 6px rgba(0,0,0,0.15),
      inset 0 -3px 5px rgba(255,255,255,0.2);
    transition:
      transform 0.25s cubic-bezier(.4,0,.2,1),
      box-shadow 0.3s ease,
      background 0.3s ease,
      border-color 0.3s ease,
      color 0.3s ease;
  }

  .link-button:hover,
  .link-button:focus {
    transform: translateY(-3px) scale(1.05);
    box-shadow:
      0 8px 15px rgba(0,0,0,0.3),
      inset 0 -3px 8px rgba(255,255,255,0.3);
    border-color: rgba(255,255,255,0.6);
    color: white; /* keep text color white on hover */
    outline: none;
  }

  /* Platform brand colors with gradient and border */
  a.link-portfolio {
    background: linear-gradient(145deg, #002244, #003366);
    border-color: #001a33;
  }

  a.link-resume {
    background: linear-gradient(145deg, #594de8, #6c63ff);
    border-color: #4a3ecf;
  }

  a.link-linkedin {
    background: linear-gradient(145deg, #005582, #0077b5);
    border-color: #004466;
  }

  a.link-email {
    background: linear-gradient(145deg, #b5392f, #d44638);
    border-color: #8b2d24;
  }

  /* Font Awesome icon size inside buttons */
  .link-button i {
    font-size: 20px;
  }
</style>

<!-- Buttons -->
<div class="button-container">
  <a href="https://ekram49.github.io/" class="link-button link-portfolio" target="_blank" rel="noopener noreferrer">
    <i class="fas fa-book"></i> Portfolio
  </a>
  <a href="https://drive.google.com/file/d/1HnU5TD-siw7CX4ezt4imaF2FTCv6M6pR/view?usp=drive_link" class="link-button link-resume" target="_blank" rel="noopener noreferrer">
    <i class="fas fa-file-alt"></i> Resume
  </a>
  <a href="https://www.linkedin.com/in/ekram-ullah-ahmed/" class="link-button link-linkedin" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-linkedin"></i> LinkedIn
  </a>
  <a href="mailto:ekramullahzaki@gmail.com" class="link-button link-email">
    <i class="fas fa-envelope"></i> Email
  </a>
</div>

<script>
  document.addEventListener("DOMContentLoaded", () => {
    const sliders = document.querySelectorAll(".image-slider");

    sliders.forEach(slider => {
      const images = JSON.parse(slider.dataset.images || "[]");
      let currentIndex = 0;

      // Fix: Inject slider HTML properly as a string
      slider.innerHTML = `
        <div class="arrow arrow-left">&#10094;</div>
        <div class="arrow arrow-right">&#10095;</div>
        <div class="slider"></div>
        <div class="slider-dots"></div>
      `;

      const sliderDiv = slider.querySelector(".slider");
      const dotsContainer = slider.querySelector(".slider-dots");
      const leftArrow = slider.querySelector(".arrow-left");
      const rightArrow = slider.querySelector(".arrow-right");

      function createImage(src) {
        const img = document.createElement("img");
        img.className = "slider-main-image";
        img.src = src;
        img.alt = "Slider Image";
        return img;
      }

      function createDots() {
        dotsContainer.innerHTML = "";
        images.forEach((_, i) => {
          const dot = document.createElement("span");
          dot.addEventListener("click", () => {
            if (i !== currentIndex) {
              const dir = i > currentIndex ? "left" : "right";
              currentIndex = i;
              updateImage(dir);
            }
          });
          dotsContainer.appendChild(dot);
        });
      }

      function updateDots() {
        const allDots = dotsContainer.querySelectorAll("span");
        allDots.forEach(dot => dot.classList.remove("active"));
        if (allDots[currentIndex]) allDots[currentIndex].classList.add("active");
      }

      function updateImage(direction) {
        const oldImg = sliderDiv.querySelector(".slider-main-image");
        const newImg = createImage(images[currentIndex]);
        newImg.style.transform = direction === "left" ? "translateX(100%)" : "translateX(-100%)";
        sliderDiv.appendChild(newImg);

        requestAnimationFrame(() => {
          newImg.style.transition = "transform 0.5s ease, opacity 0.5s ease";
          newImg.style.transform = "translateX(0)";
          if (oldImg) {
            oldImg.style.transition = "transform 0.5s ease, opacity 0.5s ease";
            oldImg.style.transform = direction === "left" ? "translateX(-100%)" : "translateX(100%)";
          }
        });

        setTimeout(() => {
          if (oldImg) oldImg.remove();
        }, 500);

        updateDots();
      }

      leftArrow.addEventListener("click", () => {
        currentIndex = (currentIndex - 1 + images.length) % images.length;
        updateImage("right");
      });

      rightArrow.addEventListener("click", () => {
        currentIndex = (currentIndex + 1) % images.length;
        updateImage("left");
      });

      // Initialize
      createDots();
      updateImage("left");
    });
  });
</script>


<!-- Your original content below (unchanged) -->

Hey, this is Ekram—a maritime data analyst with a background that spans marine engineering, pharmaceutical retail, maritime tech startups, and a lot of time spent diving deep into data. 
The sea has shaped a big part of who I am—both in work and in life. If you're curious how someone goes from engine rooms to code, from ports to platforms, stick around. Here's a bit of my journey.

<h2> Early Life </h2>

I was born on a naval base in Khulna, Bangladesh. With my father serving as a naval officer in the Bangladesh Navy, I spent my early years moving from one naval base to another. Growing up in that world gave me rare access to Navy ships, training centers, and the everyday life of sailors. While living on bases, I got to swim, dive, and ride boats with sailors and officers who felt more like family than figures in uniform. Being surrounded by the discipline, camaraderie, and quiet strength of the Navy shaped the way I saw the world—and left me with a deep longing to carve out my own path connected to the sea.

<h2> Academy Life </h2>

My journey as a maritime professional began in 2013 when I joined the prestigious Bangladesh Marine Academy as a marine engineering cadet. Over the course of two intense years of pre-sea training, I was introduced to the fundamentals of seamanship, personal survival techniques, fire prevention, marine safety, ship construction, and maritime regulations. As an engineering cadet, I also delved deep into subjects like thermodynamics, marine propulsion systems, electrical and control systems, and the inner workings of shipboard machinery.

But beyond the technical curriculum, the Academy was where I learned the value of discipline, leadership, and resilience—qualities deeply rooted in maritime and regimental life. The daily routine, the drills, the inspections, and the unspoken codes of conduct shaped not just how I worked but who I was becoming.


<div class="image-slider" 
  data-images='["https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Academy%201.png", 
  "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Academy%202.png",
  "https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/About%20Me/Ship.png"]'>
</div>


I had the privilege of learning from seasoned mariners—Captains and Chief Engineers whose stories stretched across oceans and decades. Their mentorship was as impactful as the textbooks. And equally unforgettable were my coursemates: some of the hardest-working, brilliant, and driven individuals I’ve ever met. Many now serve as officers on ships around the world, work in shore-based maritime roles, or thrive in other industries, bringing the same grit and excellence wherever they go.

<h2> Sea Life </h2>

After graduating from the Academy, I began my sea career aboard Bashundhara 7, a bulk carrier, as a trainee marine engineer. On board, I got hands-on experience with engine room operations—assisting in the maintenance of the main engine, auxiliary engines, boilers, pumps, compressors, and other vital systems. I learned how to keep the heart of the ship running, often under challenging and unpredictable conditions.

Later, I continued my training on Bashundhara 8, a sister vessel with a similar setup and sailing pattern. Between the two ships, I completed the 13 months of sea time required for cadetship, gaining exposure to a wide range of operations, watchkeeping routines, and safety drills.

Life at sea was as demanding as it was rewarding. I sailed alongside seasoned marine engineers and officers, traveled to foreign ports, and experienced the unique rhythm of life aboard a merchant vessel. I met people from different cultures, adapted to long voyages, and learned to work as part of a close-knit crew in a constantly moving environment.

Those months at sea taught me more than just engineering—they taught me discipline, resilience, teamwork, and how to stay calm when things don’t go as planned. The experience shaped my character and laid the foundation for everything that followed in both my personal and professional life.


<h2> Academy Life 2.0</h2>


After completing my sea training, I returned to the Academy for advanced marine engineering courses and certifications. This time, the theory came alive—what once seemed abstract now made perfect sense in the context of my time onboard. Concepts like thermodynamics, electrical systems, and engine room operations felt far more intuitive, and I was able to connect classroom lessons with real-life challenges I’d faced at sea.

It was also a chance to reunite with many of my coursemates. We shared our sea stories, exchanged insights, and learned from each other’s experiences on different vessels across the globe. That exchange enriched my understanding and broadened my perspective of the industry.

Alongside the coursework, I also completed a thesis on battery energy storage systems (BESS) and their integration with a ship’s power generation system. The research explored how BESS could address the limitations of conventional marine electrical systems—offering smarter power management, reducing auxiliary engine running hours, and delivering both economic and environmental benefits via fuel savings and reduced blackouts. I analyzed control strategies, engine load responses, and system design, and proposed improvements to enhance efficiency and overcome current limitations.

After successfully defending my thesis, I earned my Bachelor’s in Marine Engineering from Bangladesh Maritime University in 2019.


<h2> Tech Life </h2>

After graduation, I moved to the US and decided to pivot my career toward data analytics within the maritime industry. To build the right skill set, I completed courses in data science and analytics, where I gained expertise in statistical analysis, data visualization, SQL, Python, and tools like Tableau and Excel. Beyond the technical skills, I developed critical problem-solving abilities, effective communication, and project management techniques essential for collaborating across teams.

Combining these new skills with my maritime background helped me secure roles at innovative industry leaders like Nautilus Labs and Sofar Ocean. There, I had the privilege of working alongside some of the most talented, driven, and forward-thinking professionals I’ve ever known—people passionate about solving complex challenges in shipping and climate tech.

My work ranged from data analytics and client communications to developing tools and insights focused on voyage simulation and optimization, vessel performance monitoring, process automation, weather routing, and post-voyage reporting. I regularly collaborated with product and engineering teams—contributing to project planning, prototyping software solutions, and serving as a subject matter expert on maritime operations, shipping logistics, and voyage optimization.

My firsthand experience onboard ships proved invaluable, earning me respect from colleagues who recognized how practical maritime knowledge enhanced our solutions. I also played a key role in hiring and training new and existing team members, sharing my maritime insights to help them better understand the industry and contribute to building practical, effective products and services.


<h2> Geek Life </h2>

Outside of work, I’m pretty obsessed with the ocean—not just from a seafarer’s point of view, but also in terms of marine life and sustainability. I'm also curious about aviation, healthcare tech, and renewable energy (particularly battery innovations). Basically, if it’s data-rich and meaningful, I want to explore it.

This blog is where I share some of those explorations—data projects, visualizations, and thoughts on topics I care about.

<h2> Life(!) Life </h2>

When I’m not working or geeking out over datasets, you’ll probably find me doing kettlebell workouts, long-distance swimming, or cruising around NYC on my e-bike or electric skateboard. I’m currently working on a few personal goals: getting my scuba certification, private pilot license, and skydiving license—all within this year. Wish me luck!

If anything in my blog catches your interest—or if you just feel like saying hi—I’d love to hear from you! Doesn’t matter who you are or where you are in your journey; if you feel like connecting, you’re more than welcome to. You can always find me on [LinkedIn](https://www.linkedin.com/in/ekram-ullah-ahmed/), or you can just [email me](mailto:ekramullahzaki@gmail.com) —my inbox is always open!

P.S. I started this blog about five years ago, but didn’t pay much attention to it. Until recently, my "About Me" section still had a few lines from the default template claiming there was a movie made about me! Someone read that, got curious, endede up watching the whole movie, and was very confused until I explained it was just placeholder text.......funny, right?

I was going to remove it, but then thought... nah, I’ll just keep it as it is! If you do decide to watch the movie, just know—full disclosure—it has absolutely nothing to do with me! I hadn’t even seen it until I was asked about it......I'm no farm boy, and I definitely don't know any Buttercup! But it’s a good (kinda weird.....but good!) movie—so enjoy!

### My history

To be honest, I'm having some trouble remembering right now, so why don't you just watch [my movie](http://en.wikipedia.org/wiki/The_Princess_Bride_%28film%29) and it will answer **all** your questions.

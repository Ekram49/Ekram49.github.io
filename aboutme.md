---
layout: page
title: Ekram Ahmed 
subtitle: Maritime Data Analyst
---

<style>
  /* Your link button styles */
  .link-button {
    display: inline-block;
    margin: 5px 10px;
    padding: 8px 16px;
    background-color: #d3d3d3;
    color: #003366;
    text-decoration: none;
    border-radius: 6px;
    transition: background-color 0.3s ease, transform 0.2s ease;
  }
  .link-button:hover {
    background-color: #a9a9a9; /* darker shade */
    transform: scale(1.05);
  }

  /* Slider container */
  #image-slider {
    position: relative;
    width: 80%; /* Adjust width */
    max-width: 800px; /* Limit maximum size */
    margin: 20px auto;
    height: 400px; /* Adjust height */
    overflow: hidden;
    border-radius: 12px;
    background-color: transparent; /* Transparent background */
  }

  /* Main image styles */
  .slider-main-image {
    width: 100%;
    height: 100%;
    object-fit: contain; /* Ensure no cropping, keep aspect ratio */
    border-radius: 12px; /* Rounded corners */
    transition: transform 0.5s ease, box-shadow 0.3s ease;
  }

  /* Arrow button styles */
  .arrow {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: rgba(0, 0, 0, 0.6);
    color: white;
    padding: 15px;
    border-radius: 50%;
    font-size: 25px;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.3);
  }

  .arrow:hover {
    transform: translateY(-50%) scale(1.2);
    box-shadow: 2px 2px 15px rgba(0, 0, 0, 0.6);
  }

  .arrow-left {
    left: 10px;
  }

  .arrow-right {
    right: 10px;
  }

  /* Hover zoom effect on main image */
  #image-slider:hover .slider-main-image {
    transform: scale(1.05); /* Slight zoom */
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3); /* Shadow for "card-like" effect */
  }

  /* Dots navigation */
  .slider-dots {
    position: absolute;
    bottom: 10px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 10px;
    z-index: 20;
  }

  .slider-dots span {
    display: block;
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background-color: white; /* Solid white color */
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .slider-dots span.active {
    background-color: rgba(0, 0, 0, 0.8); /* Darker shade for active dot */
  }
</style>

<!-- Slider JavaScript -->
<script>
  document.addEventListener("DOMContentLoaded", function() {
    const sliderDiv = document.querySelector("#image-slider");
    const imageLinks = JSON.parse(sliderDiv.getAttribute("data-images"));

    const sliderHTML = `
      <img class="slider-main-image" src="${imageLinks[0]}" alt="Main Image">
      <div class="arrow arrow-left">&#8592;</div>
      <div class="arrow arrow-right">&#8594;</div>
      <div class="slider-dots">
        ${imageLinks.map((_, index) => `<span data-index="${index}"></span>`).join('')}
      </div>
    `;
    sliderDiv.innerHTML = sliderHTML;

    let currentIndex = 0;
    const mainImage = document.querySelector(".slider-main-image");
    const leftArrow = document.querySelector(".arrow-left");
    const rightArrow = document.querySelector(".arrow-right");
    const dots = document.querySelectorAll(".slider-dots span");

    // Function to update the main image with sliding animation (new image comes from the right)
    function updateMainImage(index) {
      // Move current image to the left
      mainImage.style.transition = "transform 0.5s ease-in-out";
      mainImage.style.transform = `translateX(-100%)`; // Slide out old image

      setTimeout(() => {
        mainImage.src = imageLinks[index]; // Update image
        mainImage.style.transition = "transform 0.5s ease-in-out"; // Reset animation
        mainImage.style.transform = `translateX(100%)`; // Position new image to the right
      }, 500); // Wait for the slide-out transition to complete

      // Animate the new image coming from the right
      setTimeout(() => {
        mainImage.style.transform = `translateX(0)`; // Slide in new image from the right
      }, 10); // Small delay for the new image to appear smoothly

      // Update the dots
      dots.forEach(dot => dot.classList.remove('active'));
      dots[index].classList.add('active');
    }

    // Thumbnail dot click event
    dots.forEach((dot) => {
      dot.addEventListener("click", () => {
        const dotIndex = parseInt(dot.getAttribute("data-index"));
        currentIndex = dotIndex;
        updateMainImage(currentIndex);
      });
    });

    // Arrow navigation with smooth slide
    leftArrow.addEventListener("click", () => {
      currentIndex = (currentIndex === 0) ? imageLinks.length - 1 : currentIndex - 1;
      updateMainImage(currentIndex);
    });

    rightArrow.addEventListener("click", () => {
      currentIndex = (currentIndex === imageLinks.length - 1) ? 0 : currentIndex + 1;
      updateMainImage(currentIndex);
    });

    // Auto sliding functionality
    let slideInterval;

    function autoSlide() {
      slideInterval = setInterval(() => {
        currentIndex = (currentIndex === imageLinks.length - 1) ? 0 : currentIndex + 1;
        updateMainImage(currentIndex);
      }, 5000); // Change image every 5 seconds
    }

    // Stop auto-slide when hovering over the slider
    function stopAutoSlide() {
      clearInterval(slideInterval);
    }

    // Start auto-sliding images
    autoSlide();

    // Pause auto slide when hovering over the slider
    sliderDiv.addEventListener("mouseenter", stopAutoSlide);
    sliderDiv.addEventListener("mouseleave", autoSlide);
  });
</script>

<!-- Main Content Starts Here -->
<div style="text-align: center; margin-top: 10px; margin-bottom: 30px;">
  <a href="https://ekram49.github.io/" class="link-button">Portfolio</a>
  <a href="https://drive.google.com/file/d/1HnU5TD-siw7CX4ezt4imaF2FTCv6M6pR/view?usp=drive_link" class="link-button">Resume</a>
  <a href="https://www.linkedin.com/in/ekram-ullah-ahmed/" class="link-button">LinkedIn</a>
  <a href="mailto:ekramullahzaki@gmail.com" class="link-button">Email</a>
</div>

Hey, this is Ekram—a maritime data analyst with a background that spans marine engineering, pharmaceutical retail, maritime tech startups, and a lot of time spent diving deep into data. 
The sea has shaped a big part of who I am—both in work and in life. If you're curious how someone goes from engine rooms to code, from ports to platforms, stick around. Here's a bit of my journey.

<h2> Early Life </h2>

I was born on a naval base in Khulna, Bangladesh. With my father serving as a naval officer in the Bangladesh Navy, I spent my early years moving from one naval base to another. Growing up in that world gave me rare access to Navy ships, training centers, and the everyday life of sailors. While living on bases, I got to swim, dive, and ride boats with sailors and officers who felt more like family than figures in uniform. Being surrounded by the discipline, camaraderie, and quiet strength of the Navy shaped the way I saw the world—and left me with a deep longing to carve out my own path connected to the sea.

<h2> Academy Life </h2>

My journey as a maritime professional began in 2013 when I joined the prestigious Bangladesh Marine Academy as a marine engineering cadet. Over the course of two intense years of pre-sea training, I was introduced to the fundamentals of seamanship, personal survival techniques, fire prevention, marine safety, ship construction, and maritime regulations. As an engineering cadet, I also delved deep into subjects like thermodynamics, marine propulsion systems, electrical and control systems, and the inner workings of shipboard machinery.

But beyond the technical curriculum, the Academy was where I learned the value of discipline, leadership, and resilience—qualities deeply rooted in maritime and regimental life. The daily routine, the drills, the inspections, and the unspoken codes of conduct shaped not just how I worked but who I was becoming.


<div id="image-slider" 
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

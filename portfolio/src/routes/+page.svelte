<script>
  import Icon from "@iconify/svelte";
  import { fly } from "svelte/transition";

  const skills = {
    Frontend: [
      { name: "JavaScript", icon: "logos:javascript" },
      { name: "TypeScript", icon: "logos:typescript-icon" },
      { name: "HTML5", icon: "logos:html-5" },
      { name: "CSS3", icon: "logos:css-3" },
      { name: "React.js", icon: "logos:react" },
      { name: "Angular", icon: "logos:angular-icon" },
      { name: "Svelte", icon: "logos:svelte-icon" },
    ],
    Mobile: [
      { name: "Flutter (Dart)", icon: "logos:flutter" },
      { name: "React Native", icon: "logos:react" },
    ],
    Backend: [
      { name: ".NET", icon: "logos:dotnet" },
      { name: "PHP", icon: "logos:php" },
      { name: "Java", icon: "logos:java" },
    ],
    Tools: [
      { name: "Git", icon: "logos:git-icon" },
      { name: "GitHub", icon: "mdi:github" },
      { name: "MySQL", icon: "logos:mysql" },
      { name: "MongoDB", icon: "logos:mongodb-icon" },
      { name: "Docker", icon: "logos:docker-icon" },
      { name: "REST APIs" },
      { name: "CI/CD (Vercel, GitHub)" },
    ],
  };

  const projects = [
    {
      title: "MoodTracker",
      slug: "moodtracker",
      description: "PWA to track daily mood and journal using Angular.",
      image: "very-happy.png",
    },
    {
      title: "Bookkeeper",
      slug: "bookkeeper",
      description: "React Native app to log and organize your reading journey.",
      image: "bookkeeper.png",
    },
    {
      title: "Warehouse Manager",
      slug: "warehouse-app",
      description:
        "Flutter-based Android app for barcode scanning and inventory control.",
    },
  ];
</script>

<section id="home">
  <div>
    <h1 class="name">Sarah Schurgers</h1>
    <p>Applied Computer Science student @ Hogeschool PXL.</p>
    <p>
      Passionate about frontend development, intuitive UI/UX design, and smart
      data processing.
    </p>
    <div class="socials">
      <a
        href="https://github.com/SarahSchurgersPXL"
        target="_blank"
        aria-label="GitHub"
      >
        <i class="fab fa-github"></i>
      </a>
      <a
        href="https://www.linkedin.com/in/sarahschurgers/"
        target="_blank"
        aria-label="LinkedIn"
      >
        <i class="fab fa-linkedin"></i>
      </a>
      <a href="mailto:sarahschurgers@gmail.com" aria-label="E-mail">
        <i class="fas fa-envelope"></i>
      </a>
    </div>
  </div>
</section>

<section id="skills">
  <div class="skills">
    <h2>Skills</h2>
    <div class="skills-section">
      {#each Object.entries(skills) as [category, items]}
        <div class="category">
          <h3>{category.replace(/([A-Z])/g, " $1").trim()}</h3>
          <ul class="skill-list">
            {#each items as skill}
              <li class="skill-item">
                {#if skill.icon}
                  <Icon icon={skill.icon} width="20" height="20" />
                {/if}
                {skill.name}
              </li>
            {/each}
          </ul>
        </div>
      {/each}
    </div>
  </div>
</section>

<section id="education">
  <div class="edu">
    <h2>Education</h2>
    <div class="timeline">
      <div class="entry" in:fly={{ y: 20, duration: 500 }}>
        <h3>PXL University of Applied Sciences and Arts</h3>
        <span>2022 – present</span>
        <p>
          Bachelor of Applied Computer Science (Switch2IT) – Application
          Development
        </p>
      </div>

      <div class="entry" in:fly={{ y: 20, duration: 500, delay: 300 }}>
        <h3>PXL University of Applied Sciences and Arts</h3>
        <span>2013 – 2016</span>
        <p>Bachelor of Agro- and Biotechnology – Cell and Gene Technology</p>
      </div>
    </div>
  </div>
</section>

<section id="experience">
  <div class="experience">
    <h2>Experience</h2>
    <div class="timeline">
      <div class="entry" in:fly={{ y: 20, duration: 500 }}>
        <h3>Intern</h3>
        <strong>Greenyard Prepared Belgium</strong>
        <span>March 2025 – June 2025</span>
        <p>
          Developed an Android warehouse management application using Flutter.
        </p>
      </div>

      <div class="entry" in:fly={{ y: 20, duration: 500, delay: 300 }}>
        <h3>Process Controller</h3>
        <strong>Greenyard Prepared Belgium</strong>
        <span>September 2019 – Present</span>
        <p class="line">
          Ensuring quality, inspecting raw materials, calibrating sorting
          machines,
        </p>
        <p>and performing final product quality checks.</p>
      </div>

      <div class="entry" in:fly={{ y: 20, duration: 500, delay: 600 }}>
        <h3>Consultant</h3>
        <strong>Select Projects</strong>
        <span>June 2018 – August 2019</span>
        <p>QC Chemist at Estée Lauder and R&D Assistant at Dirafrost.</p>
      </div>

      <div class="entry" in:fly={{ y: 20, duration: 500, delay: 900 }}>
        <h3>Laboratory Technologist</h3>
        <strong>Federal Public Service Finance</strong>
        <span>March 2017 – May 2018</span>
        <p>Analyzing mineral oil samples and managing LIMS.</p>
      </div>

      <div class="entry" in:fly={{ y: 20, duration: 500, delay: 1200 }}>
        <h3>Laboratory Technologist</h3>
        <strong>KU Leuven</strong>
        <span>August 2016 – December 2016</span>
        <p>In vitro tissue culture of banana plants for the gene bank.</p>
      </div>
    </div>
  </div>
</section>

<section id="projects">
  <div class="projects">
    <h2>Projects</h2>
    <div class="project-grid">
      {#each projects as project}
        <a class="project-card" href={`/projects/${project.slug}`}>
          <img
            class="single-img"
            src={project.image}
            alt="{project.title} preview"
          />
          <h2>{project.title}</h2>
          <p>{project.description}</p>
        </a>
      {/each}
    </div>
  </div>
</section>

<style>
  /* Home */
  #home {
    padding-top: 15rem;
    color: #333;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  #home p {
    margin: 4px 0;
    font-size: 1.5rem;
    color: #fff;
    text-align: center;
    max-width: 750px;
    animation: fadeIn 1s ease-in-out both;
    animation-delay: 1s;
  }

  #home a {
    color: #fff;
    font-size: 2.8rem;
    animation: fadeIn 1s ease-in-out both;
    animation-delay: 2s;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    text-decoration: none;
  }

  #home a i {
    transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  }

  #home a:hover i {
    transform: scale(1.15);
  }
  .name {
    font-size: 5rem;
    font-weight: 600;
    color: #fff;
    text-decoration: none;
    margin-top: 2rem;
    margin-bottom: 1rem;
    text-align: center;
    padding-top: 1rem;
    background: linear-gradient(
      90deg,
      #f9f9f9,
      #ffd9da,
      #ffe6de,
      #eec9d0,
      #ecdcdf
    );
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: fadeIn 1s ease-in-out both;
  }

  /* Skills */
  #skills {
    padding-top: 3rem;
    color: #fff;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding-bottom: 7rem;
  }

  #skills h2 {
    font-size: 3rem;
    margin-bottom: 0rem;
    color: #fff;
  }

  #skills h3 {
    font-size: 2rem;
    margin-bottom: 0rem;
    color: #fff;
  }
  .category {
    margin-bottom: 0.5rem;
    align-items: center;
  }

  .skill-list {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    justify-content: center;
  }
  .skills-section {
    display: flex;
    justify-content: center;
    align-items: center;
    max-width: 600px;
  }
  ul.skill-list {
    list-style: none;
    padding: 0;
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    margin-bottom: 0rem;
  }

  .skill-item {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.2);
    padding: 0.5rem 1rem;
    border-radius: 8px;
    font-weight: 500;
    animation: fadeIn 0.6s ease-in-out both;
    color: #fff;
  }

  section {
    scroll-snap-align: start;
    padding-top: 2rem;
    padding-left: 2rem;
    padding-right: 2rem;
    padding-bottom: 2rem;
    min-height: 100vh;
    box-sizing: border-box;
    overflow: auto;
    display: block;
    margin-bottom: 2rem;
  }

  section h2 {
    font-size: 2.5rem;
    text-align: center;
    margin-bottom: 1rem;
    margin-top: 1rem;
  }

  div {
    display: flex;
    flex-direction: column;
  }
  p {
    margin: 4px 0;
    font-size: 1.5rem;
    color: #fff;
    text-align: center;
    max-width: 750px;
  }

  .socials {
    display: flex;
    flex-direction: row;
    margin-top: 8px;
    gap: 15px;
    justify-content: center;
  }

  a {
    color: #fff;
    font-size: 2.8rem;
  }

  h1 {
    font-size: 3rem;
  }

  @keyframes fadeIn {
    from {
      opacity: 0;
      transform: translateY(10px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  .projects {
    display: flex;
    align-items: center;
    flex-direction: column;
  }

  .project-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 1rem;
    padding: 0 2rem;
  }

  .project-card {
    background: #f9f9f9;
    padding: 1.5rem;
    border-radius: 20px;
    text-decoration: none;
    color: inherit;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    transition:
      transform 0.2s ease,
      box-shadow 0.2s ease;
  }

  .project-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 6px 14px rgba(0, 0, 0, 0.15);
  }

  .project-card h2 {
    margin-top: 0.5rem;
    margin-bottom: 0.5rem;
    font-size: 1.5rem;
    color: #333;
  }

  .project-card p {
    margin: 0;
    font-size: 1rem;
    color: #666;
  }

  .single-img {
    width: 100%;
    height: auto;
    object-fit: contain;
    border-radius: 12px;
    margin-bottom: 1rem;
  }

  .edu {
    display: flex;
    align-items: center;
    flex-direction: column;
  }

  .timeline {
    position: relative;
    margin: 2rem 0;
    padding-left: 2rem;
    border-left: 4px solid #ccc;
  }

  .entry {
    position: relative;
    margin-bottom: 2rem;
    padding-left: 1rem;
  }

  .entry::before {
    content: "";
    position: absolute;
    left: -10px;
    top: 0;
    width: 16px;
    height: 16px;
    background-color: #353535;
    border-radius: 50%;
    border: 2px solid white;
  }

  .entry h3 {
    margin: 0;
    font-size: 1.2rem;
    color: #222;
  }

  .entry span {
    font-size: 0.9rem;
    color: #666;
  }

  .entry p {
    margin-top: 0.5rem;
    font-size: 1rem;
  }

  .experience {
    display: flex;
    align-items: center;
    flex-direction: column;
  }

  @media (max-width: 900px) {
    .name {
      font-size: 4rem;
    }

    section h2 {
      font-size: 2rem;
    }

    .skills-section {
      flex-direction: column;
      align-items: center;
    }

    .skill-list {
      justify-content: center;
    }

    .project-grid {
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    }

    p {
      margin: 4px 0;
      font-size: 1.3rem;
      color: #fff;
      text-align: center;
    }

    #home {
      padding-top: 5rem;
      color: #333;
      text-align: center;
    }

    #home p {
      margin: 4px 0;
      font-size: 1.3rem;
    }

    #home a {
      font-size: 2rem;
    }

    #home a i {
      transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    }

    #home a:hover i {
      transform: scale(1.15);
    }

    #skills {
      padding-top: 1rem;
      padding-bottom: 5rem;
      padding-left: 1rem;
      padding-right: 1rem;
    }

    .skills-section {
      display: flex;
      justify-content: center;
      align-items: center;
      max-width: 50rem;
      padding-top: 0rem;
    }

    #skills h2 {
      font-size: 2rem;
      margin-bottom: 0rem;
      color: #fff;
    }

    #skills h3 {
      font-size: 1.5rem;
      margin-bottom: 0rem;
      color: #fff;
      margin-top: 0.5rem;
    }

    ul.skill-list {
      list-style: none;
      padding: 0;
      display: flex;
      flex-wrap: wrap;
      margin-bottom: 0rem;
    }
  }
</style>

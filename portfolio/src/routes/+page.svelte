<script>
  import Icon from "@iconify/svelte";
  import {
    Timeline,
    TimelineItem,
    TimelineSeparator,
    TimelineDot,
    TimelineConnector,
    TimelineContent,
    TimelineOppositeContent,
  } from "svelte-vertical-timeline";

  import { onMount } from "svelte";

  let isMobile = false;

  onMount(() => {
    const updateViewport = () => {
      isMobile = window.innerWidth < 900;
    };

    updateViewport();
    window.addEventListener("resize", updateViewport);

    return () => window.removeEventListener("resize", updateViewport);
  });

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

  const educaction = [
    {
      title: "Bachelor of Applied Computer Science (Switch2IT)",
      period: "2022 - 2025",
      institution: "PXL University of Applied Sciences and Arts",
      specialization: "Application Development",
    },
    {
      title: "Bachelor of Agro- and Biotechnology",
      period: "2013 - 2016",
      institution: "PXL University of Applied Sciences and Arts",
      specialization: "Cell and Gene Technology",
    },
  ];

  const experiences = [
    {
      title: "Intern",
      period: "March 2025 - June 2025",
      institution: "Greenyard Prepared Belgium",
      description:
        "Developed an Android warehouse management application using Flutter.",
    },
    {
      title: "Process Controller",
      period: "September 2019 – Present",
      institution: "Greenyard Prepared Belgium",
      description:
        "Ensuring quality, inspecting raw materials, calibrating sorting machines, and performing final product quality checks.",
    },
    {
      title: "Consultant",
      period: "June 2018 – August 2019",
      institution: "Select Projects",
      description: "QC Chemist at Estée Lauder and R&D Assistant at Dirafrost.",
    },
    {
      title: "Laboratory Technologist",
      period: "March 2017 – May 2018",
      institution: "Federal Public Service Finance",
      description: "Analyzing mineral oil samples and managing LIMS.",
    },
    {
      title: "Laboratory Technologist",
      period: "August 2016 – December 2016",
      institution: "KU Leuven",
      description:
        "In vitro tissue culture of banana plants for the gene bank.",
    },
  ];

  const projects = [
    {
      title: "MoodTracker",
      slug: "moodtracker",
      description: "PWA to track daily mood and journal using Angular.",
      image: "mood.png",
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
      image: "flutter.png",
    },
  ];
</script>

<section id="home">
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
</section>

<section id="skills">
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
</section>

<section id="education">
  <h2>Education</h2>
  <Timeline position={isMobile ? "alternate" : "right"}
  style={isMobile ? "padding: 0rem;" : ""}>
    {#each educaction as edu}
      <TimelineItem style="margin-top: 2rem; margin-bottom: 1rem; padding: 0;">
        <TimelineOppositeContent
          slot="opposite-content"
          style="max-width: 25rem; margin: 0;"
        >
          <p>{edu.period}</p>
        </TimelineOppositeContent>
        <TimelineSeparator>
          <TimelineDot style="background-color: #fff; border-color:#fff;" />
          <TimelineConnector
            style="background-color: #fff; border-color:#fff;"
          />
        </TimelineSeparator>
        <TimelineContent style="margin-top: 0; max-width: 25rem;">
          <h3>{edu.title}</h3>
          <h4>{edu.specialization}</h4>
          <h5>{edu.institution}</h5>
        </TimelineContent>
      </TimelineItem>
    {/each}
  </Timeline>
</section>

<section id="experience">
  <h2>Experience</h2>
  <Timeline position={isMobile ? "alternate" : "right"}
  style={isMobile ? "padding: 0rem;" : ""}>
    {#each experiences as experience}
      <TimelineItem style="margin-top: 2rem; margin-bottom: 1rem; padding: 0;">
        <TimelineOppositeContent
          slot="opposite-content"
          style="max-width: 25rem; margin: 0;"
        >
          <p>{experience.period}</p>
        </TimelineOppositeContent>
        <TimelineSeparator>
          <TimelineDot style="background-color: #fff; border-color:#fff;" />
          <TimelineConnector
            style="background-color: #fff; border-color:#fff;"
          />
        </TimelineSeparator>
        <TimelineContent style="margin-top: 0; max-width: 25rem;">
          <h3>{experience.title}</h3>
          <h5>{experience.institution}</h5>
          <h4>{experience.description}</h4>
        </TimelineContent>
      </TimelineItem>
    {/each}
  </Timeline>
</section>

<section id="projects">
  <h2>Projects</h2>
  <div class="project-grid">
    {#each projects as project}
      <a class="project-card" href={`/projects/${project.slug}`}>
        <img
          class="single-img"
          src={project.image}
          alt="{project.title} preview"
        />
        <h3>{project.title}</h3>
        <p>{project.description}</p>
      </a>
    {/each}
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
    margin-top: 1rem;
    padding: 0rem 1rem;
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
    border: 1px solid rgba(255, 255, 255, 0.103);
    padding: 0.5rem 1rem;
    border-radius: 8px;
    font-weight: 500;
    animation: fadeIn 0.6s ease-in-out both;
    color: #fff;
  }
  .skill-item:hover {
    background: rgba(255, 255, 255, 0.103);
    border-color: rgba(255, 255, 255, 0.4);
    transform: translateY(-2px);
    transition: all 0.3s ease;
    font-weight: 550;
  }

  #skills div {
    display: flex;
    flex-direction: column;
  }
  /* Education */
  #education {
    padding-top: 4rem;
    color: #fff;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding-bottom: 2rem;
    max-width: 900px;
    margin: 0 auto;
  }
  #education h2 {
    font-size: 3rem;
    margin-bottom: 0rem;
    color: #fff;
  }

  #education h3 {
    font-size: 1.5rem;
    margin-bottom: 0rem;
    color: #fff;
    padding-bottom: 0rem;
    margin-top: 0rem;
    padding-left: 1rem;
    padding-top: 0.2rem;
  }

  #education h4 {
    font-size: 1.1rem;
    margin-bottom: 0rem;
    margin-top: 0.8rem;
    color: #fff;
    padding-bottom: 0rem;
    padding-left: 1rem;
    padding-top: 0rem;
    font-weight: 400;
    font-style: italic;
  }
  #education h5 {
    font-size: 1.3rem;
    margin-bottom: 0rem;
    margin-top: 0.8rem;
    color: #fff;
    padding-bottom: 0rem;
    padding-left: 1rem;
    padding-top: 0rem;
    font-weight: 500;
  }

  #education p {
    text-align: end;
    padding-right: 1.5rem;
    font-size: 1.5rem;
  }
  /* Experience */
  #experience {
    padding-top: 4rem;
    color: #fff;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding-bottom: 10.5rem;
    max-width: 1000px;
    margin: 0 auto;
  }
  #experience h2 {
    font-size: 3rem;
    margin-bottom: 0rem;
    color: #fff;
  }

  #experience h3 {
    font-size: 1.5rem;
    margin-bottom: 0rem;
    color: #fff;
    padding-bottom: 0rem;
    margin-top: 0rem;
    padding-left: 1rem;
    padding-top: 0.2rem;
  }

  #experience h4 {
    font-size: 1.1rem;
    margin-bottom: 0rem;
    margin-top: 0.8rem;
    color: #fff;
    padding-bottom: 0rem;
    padding-left: 1rem;
    padding-top: 0rem;
    font-weight: 400;
    font-style: italic;
  }
  #experience h5 {
    font-size: 1.3rem;
    margin-bottom: 0rem;
    margin-top: 0.8rem;
    color: #fff;
    padding-bottom: 0rem;
    padding-left: 1rem;
    padding-top: 0rem;
    font-weight: 500;
  }

  #experience p {
    text-align: end;
    padding-right: 1.5rem;
    font-size: 1.5rem;
  }

  /* Projects */
  #projects {
    padding-top: 4rem;
    color: #fff;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    padding-bottom: 10.5rem;
    max-width: 900px;
    margin: 0 auto;
  }

  #projects h2 {
    font-size: 3rem;
    margin-bottom: 1rem;
    color: #fff;
  }

  #projects h3 {
    font-size: 1.5rem;
    margin-bottom: 0rem;
    color: #fff;
    padding-bottom: 0rem;
    margin-top: 0rem;
    padding-top: 0.2rem;
    text-align: center;
  }

  #projects p {
    font-size: 1rem;
    margin-bottom: 0rem;
    margin-top: 0.8rem;
    color: #fff;
    padding-bottom: 0rem;
    padding-top: 0rem;
    font-weight: 400;
    font-style: italic;
  }

  .project-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 1rem;
    padding: 5rem 2rem;
    max-width: 900px;
  }

  .project-card {
    background: rgba(255, 255, 255, 0.1);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.014);
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

  .single-img {
    width: 100%;
    height: auto;
    object-fit: contain;
    border-radius: 12px;
    margin-bottom: 1rem;
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
      padding: 0rem 0.5rem;
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
    .skill-item {
      padding: 0.5rem 1rem;
      border-radius: 8px;
      font-weight: 400;
      font-size: medium;
    }

    #education,
    #experience {
      padding-top: 1rem;
      padding-right: 0.2rem;
      padding-left: 0.2rem;
    }

    #education h2,
    #experience h2, #skills h2 {
      margin-top: 4rem;
      font-size: 2rem;
    }

    #education h3,
    #experience h3 {
      font-size: 1.1rem;
      font-weight: 550;
      padding-left: 0.5rem;
      padding-right: 0rem;
    }

    #education h4,
    #experience h4 {
      font-size: 1rem;
      padding-left: 0.5rem;
      padding-right: 0rem;
    }
    #education h5,
    #experience h5 {
      font-size: 1rem;
      padding-left: 0.5rem;
      padding-right: 0rem;
    }
    #education p,
    #experience p {
      text-align: end;
      padding-right: 1.5rem;
      font-size: 1.1rem;
    }

    #projects h2 {
      margin-top: 4rem;
      font-size: 2rem;
      margin-top: 0;
      padding-bottom: 1rem;
    }

    #projects {
      padding-bottom: 5rem;
    }
    .project-grid {
      grid-template-columns: 1fr;
      max-width: 100%;
      padding: 0 0.5rem;
    }
  }
</style>

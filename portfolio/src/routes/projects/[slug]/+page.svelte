<script lang="ts">
  export let data: { slug: string };
  const { slug } = data;
  import { onMount, onDestroy } from "svelte";
  import EmblaCarousel from "embla-carousel";
  import Autoplay from "embla-carousel-autoplay";
  import Icon from "@iconify/svelte";

  let emblaNode: HTMLDivElement;
  let embla: any;
  let autoplay: any;

  let selectedIndex = 0;

  function scrollPrev() {
    embla && embla.scrollPrev();
  }
  function scrollNext() {
    embla && embla.scrollNext();
  }
  function scrollTo(index: number) {
    embla && embla.scrollTo(index);
  }

  function updateSelected() {
    if (embla) selectedIndex = embla.selectedScrollSnap();
  }

  onMount(() => {
    autoplay = Autoplay({ delay: 4000, stopOnInteraction: true });
    const viewport = emblaNode.querySelector(".embla__viewport");
    if (viewport) {
      embla = EmblaCarousel(viewport as HTMLElement, { loop: true }, [
        autoplay,
      ]);
      embla.on("select", updateSelected);
      updateSelected();
    }
    return () => {
      embla && embla.destroy();
    };
  });

  onDestroy(() => {
    embla && embla.destroy();
  });

  type Project = {
    title: string;
    description: string;
    tech: readonly string[];
    images?: string[];
  };

  const projectDetails = {
    bookkeeper: {
      title: "Bookkeeper",
      description: `
      Bookkeeper is a React Native mobile application I developed as a practice project to strengthen my app development skills.
      The app allows users to organize and log their reading journey using three categories: 'To Read', 'Currently Reading', and 'Read'. 
      Users can search for books using an external API, track their reading progress, and add personal notes. 
      This project helped me improve my understanding of navigation, state management, and API integration in a cross-platform environment using Expo and TypeScript.
    `,
      tech: ["React Native", "TypeScript", "Expo"],
      images: [
        "bookkeeper.jpg",
        "bookkeeper3.jpg",
        "bookkeeper4.jpg",
        "bookkeeper2.jpg",
      ],
    },
    "warehouse-app": {
      title: "Warehouse Manager",
      description: `
      This project was developed during my internship at Greenyard Prepared Belgium.
      Warehouse Manager is a Flutter-based Android application built to support internal warehouse operations. 
      The app is designed to work with Zebra MC9401 devices for barcode scanning, and facilitates stock movement logging and inventory management.
    `,
      tech: ["Flutter", "Dart", "Git"],
    },
    moodtracker: {
      title: "MoodTracker",
      description: `
      MoodTracker is a Progressive Web App that enables users to log their daily mood using five expressive icons and optional notes.
      Built with Angular and hosted on Vercel, the app works offline, can be installed on mobile devices, and stores data securely using Supabase, which also handles user authentication.
      This project gave me hands-on experience with building PWA functionality, implementing modern UI/UX principles, and connecting frontend logic with a real-time backend.
    `,
      tech: ["Angular", "TypeScript", "PWA", "Supabase", "Vercel", "GitHub"],
      images: [
        "moodtracker.png",
        "moodtracker2.png",
        "moodtracker-detail.png",
        "moodtracker-line.png",
        "moodtracker-month.png",
        "moodtracker-pie.png",
      ],
    },
  } as const;

  type ProjectKey = keyof typeof projectDetails;
  const project = projectDetails[slug as ProjectKey] as Project;

  const images = project.images ?? [];

  const techIcons: Record<string, string> = {
    "React Native": "mdi:react",
    Expo: "simple-icons:expo",
    TypeScript: "mdi:language-typescript",
    Flutter: "simple-icons:flutter", // <-- use simple-icons for Flutter
    Angular: "mdi:angular",
    PWA: "mdi:progress-wrench",
    Supabase: "simple-icons:supabase",
    Vercel: "simple-icons:vercel",
    GitHub: "mdi:github",
    Dart: "simple-icons:dart",
    Git: "mdi:git",
  };
</script>

<div class="project">
  {#if project}
    <div class="project-detail">
      <h1 class="project-title">{project.title}</h1>
      <p class="description">{project.description}</p>

      <h3>Technologies used:</h3>
      <ul class="tech-list">
        {#each project.tech as t}
          <li>
            {#if techIcons[t]}
              <Icon
                icon={techIcons[t]}
                width="1.5em"
                height="1.5em"
                style="vertical-align: middle; margin-right: 0.5em;"
              />
            {/if}
            {t}
          </li>
        {/each}
      </ul>
    </div>
    {#if images.length}
      <div class="embla__controls-side">
        <button
          class="embla__button"
          on:click={scrollPrev}
          aria-label="Previous image"
        >
          <!-- Left Arrow SVG -->
          <svg width="28" height="28" viewBox="0 0 24 24" fill="none">
            <path
              d="M15 18l-6-6 6-6"
              stroke="#fff"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </button>
        <div class="embla__carousel-wrapper">
          <div class="embla" bind:this={emblaNode}>
            <div class="embla__viewport">
              <div class="embla__container">
                {#each images as image}
                  <div class="embla__slide">
                    <img
                      class="carousel-img"
                      src={`/${image}`}
                      alt={project.title}
                    />
                  </div>
                {/each}
              </div>
            </div>
          </div>
          <div class="embla__dots">
            {#each images as _, idx}
              <button
                class="embla__dot {selectedIndex === idx ? 'is-selected' : ''}"
                aria-label={`Go to slide ${idx + 1}`}
                on:click={() => scrollTo(idx)}
              ></button>
            {/each}
          </div>
        </div>
        <button
          class="embla__button"
          on:click={scrollNext}
          aria-label="Next image"
        >
          <!-- Right Arrow SVG -->
          <svg width="28" height="28" viewBox="0 0 24 24" fill="none">
            <path
              d="M9 6l6 6-6 6"
              stroke="#fff"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </button>
      </div>
    {/if}
  {:else}
    <div class="not-found">
      <h1>Project not found</h1>
      <p>We couldn't find a project with the slug <strong>{slug}</strong>.</p>
    </div>
  {/if}
</div>

<style>
  .project {
    padding-top: 3rem;
    color: #fff;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding-bottom: 7rem;
    max-width: 900px;
    margin: 0 auto;
  }
  h1 {
    font-size: 3rem;
    margin-bottom: 0rem;
    color: #fff;
  }
  .project-detail {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
  }
  .project-title {
    font-size: 50px;
    margin-bottom: 20px;
  }

  .description {
    font-size: 20px;
    margin-bottom: 20px;
    display: flex;
    flex-wrap: wrap;
    max-width: 700px;
  }

  .embla {
    overflow: hidden;
    width: 100%;
    max-width: 600px;
    margin: 1rem auto;
  }
  .embla__viewport {
    overflow: hidden;
    width: 100%;
  }
  .embla__container {
    display: flex;
  }
  .embla__slide {
    position: relative;
    flex: 0 0 100%;
    min-width: 0;
    display: flex;
    justify-content: center;
    align-items: start;
  }
  .carousel-img {
    width: 100%;
    max-width: 25rem;
    height: auto;
    display: block;
    margin: 0 auto;
    border-radius: 12px;
  }

  .embla__button {
    background: #fff2;
    border: none;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #fff;
    font-size: 2rem;
    border-radius: 50%;
    width: 2.5rem;
    height: 2.5rem;
    cursor: pointer;
    transition: background 0.2s;
    padding: 0;
  }
  .embla__button:hover {
    background: #fa987d;
    color: #fff;
  }
  .embla__dots {
    display: flex;
    justify-content: center;
    gap: 0.5rem;
    margin-top: 1rem;
  }
  .embla__dot {
    width: 0.9rem;
    height: 0.9rem;
    border-radius: 50%;
    border: none;
    background: #fff4;
    cursor: pointer;
    transition: background 0.2s;
  }
  .embla__dot.is-selected,
  .embla__dot:hover {
    background: #fa987d;
  }

  .embla__controls-side {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 1.5rem;
    margin: 2rem 0 1rem 0;
  }

  .embla__carousel-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 28rem;
    width: 100%;
  }

  .tech-list {
    list-style: none;
    padding: 0;
    display: flex;
    flex-wrap: wrap;
    gap: 1.2rem;
    justify-content: center;
  }
  .tech-list li {
    display: flex;
    align-items: center;
    font-size: 1.1rem;
    color: #fff;
  }

  @media (max-width: 900px) {
    .project-title {
      font-size: 2.5rem;
      margin-bottom: 0;
    }
    .description {
      font-size: 1.1rem;
    }  
    .project-detail,
    .embla__controls-side {
      padding-left: 1rem;
      padding-right: 1rem;
    }
    .embla__button {
      width: 3rem;
      height: 3rem;
      font-size: 2.2rem;
      min-width: 3rem;
      min-height: 3rem;
    }
    .embla__controls-side {
      gap: 0.5rem;
    }
  }
</style>

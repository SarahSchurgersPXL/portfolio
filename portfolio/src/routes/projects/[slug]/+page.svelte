<script lang="ts">
  export let data: { slug: string };
  const { slug } = data;
  import { onMount, onDestroy } from 'svelte';
  import emblaCarouselSvelte from "embla-carousel-svelte";
  import EmblaCarousel from 'embla-carousel';
  import Autoplay from "embla-carousel-autoplay";

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
    const viewport = emblaNode.querySelector('.embla__viewport');
    if (viewport) {
      embla = EmblaCarousel(viewport as HTMLElement, { loop: true }, [autoplay]);
      embla.on('select', updateSelected);
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
      description: "React Native app to log and organize your reading journey.",
      tech: ["React Native", "Expo", "TypeScript"],
      images: [
        "bookkeeper.jpg",
        "bookkeeper2.jpg",
        "bookkeeper3.jpg",
        "bookkeeper4.jpg",
      ],
    },
    "warehouse-app": {
      title: "Warehouse Manager",
      description:
        "Flutter-based Android app for barcode scanning and inventory control.",
      tech: ["Flutter"],
    },
    moodtracker: {
      title: "MoodTracker",
      description:
        "MoodTracker is a Progressive Web App that lets users log their daily moods using five icons and optional notes. Built with Angular and hosted on Vercel, the app works offline and can be installed on mobile devices. Data is stored securely in Supabase, which also handles user authentication.",
      tech: ["Angular", "PWA", "TypeScript"],
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
</script>

<div class="project">
  {#if project}
    <div class="project-detail">
      <h1 class="project-title">{project.title}</h1>
      <p class="description">{project.description}</p>

      <h3>Technologies used:</h3>
      <ul class="tech-list">
        {#each project.tech as t}
          <li>{t}</li>
        {/each}
      </ul>
    </div>
    {#if images.length}
  <div class="embla__controls-side">
    <button class="embla__button" on:click={scrollPrev} aria-label="Previous image">
      <!-- Left Arrow SVG -->
      <svg width="28" height="28" viewBox="0 0 24 24" fill="none">
        <path d="M15 18l-6-6 6-6" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </button>
    <div class="embla__carousel-wrapper">
      <div class="embla" bind:this={emblaNode}>
        <div class="embla__viewport">
          <div class="embla__container">
            {#each images as image}
              <div class="embla__slide">
                <img class="carousel-img" src={`/${image}`} alt={project.title} />
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
    <button class="embla__button" on:click={scrollNext} aria-label="Next image">
      <!-- Right Arrow SVG -->
      <svg width="28" height="28" viewBox="0 0 24 24" fill="none">
        <path d="M9 6l6 6-6 6" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
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
    max-width: 600px;
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
    flex: 0 0 100%; /* Show 1 slide at a time */
    min-width: 0;
    display: flex;
    justify-content: center; /* Center image horizontally */
    align-items: start;     /* Center image vertically if you want */
  }
  .carousel-img {
    width: 100%;      /* Fill the slide */
    max-width: 25rem; /* Optional: limit image size */
    height: auto;
    display: block;
    margin: 0 auto;   /* Center if image is smaller than slide */
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
</style>

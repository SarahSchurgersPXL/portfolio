<script lang="ts">
  export let data: { slug: string };
  const { slug } = data;

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
      ]
    },
  } as const;

  type ProjectKey = keyof typeof projectDetails;
  const project = projectDetails[slug as ProjectKey];
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
</style>

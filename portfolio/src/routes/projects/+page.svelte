<script>
  const projects = [
    {
      title: "MoodTracker",
      slug: "moodtracker",
      description: "PWA to track daily mood and journal using Angular.",
      images: [
        "angry.png",
        "sad.png",
        "neutral.png",
        "happy.png",
        "very-happy.png",
      ],
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

<div class="projects">
  <h1>Projects</h1>

  <div class="project-grid">
    {#each projects as project}
      <a class="project-card" href={`/projects/${project.slug}`}>
        {#if project.images}
          <div class="image-row">
            {#each project.images as img}
              <img src={img} alt="MoodTracker preview" />
            {/each}
          </div>
        {:else if project.image}
          <img
            class="single-img"
            src={project.image}
            alt="{project.title} preview"
          />
        {/if}
        <h2>{project.title}</h2>
        <p>{project.description}</p>
      </a>
    {/each}
  </div>
</div>

<style>
  .projects {
    display: flex;
    align-items: center;
    flex-direction: column;
    margin-top: 50px;
  }

  h1 {
    font-size: 50px;
    text-align: center;
    margin-bottom: 30px;
  }

  .project-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
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

  .image-row {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 0.5rem;
    overflow-x: auto;
    margin-bottom: 1rem;
    margin-top: 3.3rem;
  }

  .image-row img {
    width: 75px;
    height: 75px;
    object-fit: cover;
    border-radius: 8px;
  }

  .single-img {
    width: 100%;
    max-height: 200px;
    object-fit: contain;
    border-radius: 12px;
    margin-bottom: 1rem;
  }
</style>

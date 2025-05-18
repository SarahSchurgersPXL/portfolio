<script>
  const projects = [
    { title: 'Mood Tracker', slug: 'moodtracker', description: 'Mood Tracker PWA' },
    { title: 'Bookkeeper', slug: 'bookkeeper', description: 'React Native app om boeken te loggen' }
  ];
</script>

<h1>Projects</h1>
<ul>
  {#each projects as project}
    <li>
      <a href={`/projects/${project.slug}`}>{project.title}</a>
      <p>{project.description}</p>
    </li>
  {/each}
</ul>

<script>
  export let params;
  const { slug } = params;

  const projectDetails = {
    'boekenlog': {
      title: 'Boekenlog',
      description: 'App gemaakt in React Native om boeken te beheren.',
      tech: ['React Native', 'Expo', 'TypeScript'],
    },
    'barcode-scanner': {
      title: 'Barcode Scanner',
      description: 'Flutter-app met barcode functionaliteit.',
      tech: ['Flutter', 'MVVM', 'Zebra Scanner'],
    }
  };

  const project = projectDetails[slug];
</script>

{#if project}
  <h1>{project.title}</h1>
  <p>{project.description}</p>
  <h3>Gebruikte technologieën:</h3>
  <ul>
    {#each project.tech as t}
      <li>{t}</li>
    {/each}
  </ul>
{:else}
  <h1>Project niet gevonden</h1>
{/if}

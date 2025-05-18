<script>
  import Icon from '@iconify/svelte';

  const skills = {
    Frontend: [
      { name: 'JavaScript', icon: 'logos:javascript' },
      { name: 'TypeScript', icon: 'logos:typescript-icon' },
      { name: 'HTML5', icon: 'logos:html-5' },
      { name: 'CSS3', icon: 'logos:css-3' },
      { name: 'React.js', icon: 'logos:react' },
      { name: 'Angular', icon: 'logos:angular-icon' },
      { name: 'Svelte', icon: 'logos:svelte-icon' },  
    ],
    Mobile: [
      { name: 'Flutter (Dart)', icon: 'logos:flutter' },
      { name: 'React Native', icon: 'logos:react' }
    ],
    Backend: [
      { name: '.NET', icon: 'logos:dotnet' },
      { name: 'PHP', icon: 'logos:php' },
      { name: 'Java', icon: 'logos:java' }
    ],
    Tools: [
      { name: 'Git', icon: 'logos:git-icon' },
      { name: 'GitHub', icon: 'mdi:github' },
      { name: 'MySQL', icon: 'logos:mysql' },
      { name: 'MongoDB', icon: 'logos:mongodb-icon' },
      { name: 'Docker', icon: 'logos:docker-icon' },
      { name: 'REST APIs' },
      { name: 'CI/CD (Vercel, GitHub)'}
    ]
  };
</script>

<style>
    .skills {
        display: flex;
        align-items: center;
        flex-direction: column;
        margin-top: 50px;
    }

    h1 {
        font-size: 50px;
    }

  .skills-section {
    padding: 2rem;
  }

  .category {
    margin-bottom: 2rem;
  }

  .category h2 {
    font-size: 1.5rem;
    margin-bottom: 1rem;
    color: #333;
  }

  ul.skill-list {
    list-style: none;
    padding: 0;
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
  }

  .skill-item {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    background-color: #e3e3e3;
    padding: 0.5rem 1rem;
    border-radius: 8px;
    font-weight: 500;
    animation: fadeIn 0.6s ease-in-out both;
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
</style>

<div class="skills">
    <h1>
        Skills
    </h1>
    <div class="skills-section">
    {#each Object.entries(skills) as [category, items]}
        <div class="category">
        <h2>{category.replace(/([A-Z])/g, ' $1').trim()}</h2>
        <ul class="skill-list">
            {#each items as skill}
            <li class="skill-item">
                <Icon icon={skill.icon} width="20" height="20" />
                {skill.name}
            </li>
            {/each}
        </ul>
        </div>
    {/each}
    </div>
</div>
<script>
    import { onMount } from 'svelte';
    let menuOpen = false;
    let activeSection = 'home';

    // List of section IDs in order
    const sectionIds = ['skills', 'education', 'experience', 'projects'];

    onMount(() => {
        // Add 'home' if you have a #home section
        const allSections = ['home', ...sectionIds]
            .map(id => document.getElementById(id))
            .filter(Boolean);

        const observer = new IntersectionObserver(
            (entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        activeSection = entry.target.id;
                    }
                });
            },
            { threshold: 0.5 }
        );
        // @ts-ignore
        allSections.forEach(section => observer.observe(section));
        return () => observer.disconnect();
    });
</script>

<style global>
  @import '$lib/styles/global.css';
  nav {
    position: sticky;
    top: 0;
    z-index: 100;
    background: #f8f9fa;
  }
  .nav-link.active {
    background: #e9ecef;
    color: #353535 !important;
    border-radius: 4px;
    transition: background 0.2s;
  }
</style>

<nav>
  <div class="nav-container">
    <a href="#home" class="nav-link-brand">Sarah Schurgers</a>
    <div class="nav-links {menuOpen ? 'open' : ''}">
      <a href="#skills" class="nav-link" class:active={activeSection === 'skills'}><i class="fas fa-lightbulb"></i> Skills</a>      
      <a href="#education" class="nav-link" class:active={activeSection === 'education'}><i class="fas fa-graduation-cap"></i> Education</a>
      <a href="#experience" class="nav-link" class:active={activeSection === 'experience'}><i class="fas fa-briefcase"></i> Experience</a>
      <a href="#projects" class="nav-link" class:active={activeSection === 'projects'}><i class="fas fa-code"></i> Projects</a>
    </div>
    <div class="hamburger" on:click={() => menuOpen = !menuOpen}>
      <span></span>
      <span></span>
      <span></span>
    </div>
  </div>
</nav>

<main>
    <slot />
</main>
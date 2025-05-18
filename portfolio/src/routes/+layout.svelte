<script>
	let menuOpen = false;
</script>

<style global>
  @import '$lib/styles/global.css';
</style>

<nav>
  <div class="nav-container">
    <a href="/" class="nav-link-brand">Sarah Schurgers</a>
    <div class="nav-links {menuOpen ? 'open' : ''}">
      <a href="/skills" class="nav-link">
        <i class="fas fa-lightbulb"></i> Skills
      </a>
      <a href="/projects" class="nav-link">
        <i class="fas fa-code"></i> Projects
      </a>
      <a href="/education" class="nav-link">
        <i class="fas fa-graduation-cap"></i> Education
      </a>   
      <a href="/experience" class="nav-link">
        <i class="fas fa-briefcase"></i> Experience
      </a>
       
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
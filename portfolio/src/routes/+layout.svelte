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
      <a href="/skills" class="nav-link">Skills</a>
      <a href="/projects" class="nav-link">Projects</a>
      <a href="/experience" class="nav-link">Experience</a>
      <a href="/education" class="nav-link">Education</a>    
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
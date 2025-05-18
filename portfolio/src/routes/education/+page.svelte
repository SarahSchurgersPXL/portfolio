<script>
  import { fly } from 'svelte/transition';
</script>

<style>

    .edu {
        display: flex;
        align-items: center;
        flex-direction: column;
        margin-top: 50px;
    }

    h1 {
        font-size: 50px;
    }

  .timeline {
    position: relative;
    margin: 2rem 0;
    padding-left: 2rem;
    border-left: 4px solid #ccc;
  }

  .entry {
    position: relative;
    margin-bottom: 2rem;
    padding-left: 1rem;
  }

  .entry::before {
    content: '';
    position: absolute;
    left: -10px;
    top: 0;
    width: 16px;
    height: 16px;
    background-color: #353535;
    border-radius: 50%;
    border: 2px solid white;
  }

  .entry h3 {
    margin: 0;
    font-size: 1.2rem;
    color: #222;
  }

  .entry span {
    font-size: 0.9rem;
    color: #666;
  }

  .entry p {
    margin-top: 0.5rem;
    font-size: 1rem;
  }
</style>

<div class="edu">
    <h1>
        Education
    </h1>
    <div class="timeline">
        <div class="entry" in:fly="{{ y: 20, duration: 500 }}">
            <h3>PXL University of Applied Sciences and Arts</h3>
            <span>2022 – present</span>
            <p>Bachelor of Applied Computer Science (Switch2IT) – Application Development</p>
        </div>

        <div class="entry" in:fly="{{ y: 20, duration: 500, delay: 300 }}">
            <h3>PXL University of Applied Sciences and Arts</h3>
            <span>2013 – 2016</span>
            <p>Bachelor of Agro- and Biotechnology – Cell and Gene Technology</p>
        </div>
    </div>
</div>
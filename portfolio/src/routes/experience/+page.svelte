<script>
    import { fly } from "svelte/transition";
</script>

<div class="experience">
    <h1>Experience</h1>
    <div class="timeline">
        <div class="entry" in:fly={{ y: 20, duration: 500 }}>
            <h3>Intern</h3>
            <strong>Greenyard Prepared Belgium</strong>
            <span>March 2025 – June 2025</span>
            <p>
                Developed an Android warehouse management application using Flutter.
            </p>
        </div>

        <div class="entry" in:fly={{ y: 20, duration: 500, delay: 300 }}>
            <h3>Process Controller</h3>
            <strong>Greenyard Prepared Belgium</strong>
            <span>September 2019 – Present</span>
            <p class="line">
                Ensuring quality, inspecting raw materials, calibrating sorting machines,
                
            </p>
            <p>
                and performing final product quality checks.
            </p>
        </div>

        <div class="entry" in:fly={{ y: 20, duration: 500, delay: 600 }}>
            <h3>Consultant</h3>
            <strong>Select Projects</strong>
            <span>June 2018 – August 2019</span>
            <p>
                QC Chemist at Estée Lauder and R&D Assistant at Dirafrost.
            </p>
        </div>

        <div class="entry" in:fly={{ y: 20, duration: 500, delay: 900 }}>
            <h3>Laboratory Technologist</h3>
            <strong>Federal Public Service Finance</strong>
            <span>March 2017 – May 2018</span>
            <p>
                Analyzing mineral oil samples and managing LIMS.
            </p>
        </div>

        <div class="entry" in:fly={{ y: 20, duration: 500, delay: 1200 }}>
            <h3>Laboratory Technologist</h3>
            <strong>KU Leuven</strong>
            <span>August 2016 – December 2016</span>
            <p>
                In vitro tissue culture of banana plants for the gene bank.
            </p>
        </div>
    </div>
</div>

<style>
    .experience {
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
        content: "";
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

    .entry strong {
        display: block;
        font-size: 1rem;
        color: #444;
        margin-top: 0.2rem;
    }

    .entry span {
        font-size: 0.9rem;
        color: #666;
        display: block;
        margin-top: 0.1rem;
    }

    .entry p {
        margin-top: 0.5rem;
        font-size: 1rem;
    }

    .line{
        margin-top: 0px;
        font-size: 1rem;
        margin-bottom: 0px;
    }

</style>

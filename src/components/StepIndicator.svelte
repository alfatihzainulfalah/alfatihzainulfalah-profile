<script>
  import { onMount, onDestroy } from 'svelte';

  export let steps = [];

  let activeIndex = 0;
  let observer;

  onMount(() => {
    const targets = steps
      .map((step) => document.getElementById(step.id))
      .filter(Boolean);

    observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            const index = targets.indexOf(entry.target);
            if (index !== -1) activeIndex = index;
          }
        });
      },
      { rootMargin: '-45% 0px -45% 0px', threshold: 0 }
    );

    targets.forEach((target) => observer.observe(target));
  });

  onDestroy(() => {
    if (observer) observer.disconnect();
  });

  function goTo(id) {
    document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' });
  }
</script>

<style>
  .step-indicator {
    position: fixed;
    left: 22px;
    top: 50%;
    transform: translateY(-50%);
    z-index: 20;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .step {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    padding: 7px 0;
    background: none;
    border: none;
    cursor: pointer;
    -webkit-tap-highlight-color: transparent;
  }

  .dot {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: var(--border);
    transition: background 0.25s ease, transform 0.25s ease;
  }

  .step.active .dot {
    background: var(--primary-dark);
    transform: scale(1.4);
  }

  .connector {
    width: 1px;
    height: 18px;
    background: var(--border);
    overflow: hidden;
  }

  .connector-fill {
    width: 100%;
    height: 0%;
    background: var(--primary-dark);
    transition: height 0.45s cubic-bezier(0.4, 0, 0.2, 1);
  }

  @media (max-width: 900px) {
    .step-indicator {
      display: none;
    }
  }
</style>

<nav class="step-indicator" aria-label="Section navigation">
  {#each steps as step, i}
    <button
      type="button"
      class="step"
      class:active={i === activeIndex}
      on:click={() => goTo(step.id)}
      aria-label={`Go to ${step.label}`}
      aria-current={i === activeIndex ? 'true' : undefined}
    >
      <span class="dot"></span>
    </button>
    {#if i < steps.length - 1}
      <span class="connector">
        <span class="connector-fill" style="height: {i < activeIndex ? '100%' : '0%'}"></span>
      </span>
    {/if}
  {/each}
</nav>

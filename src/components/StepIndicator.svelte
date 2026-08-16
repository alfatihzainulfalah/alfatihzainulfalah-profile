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
    right: 28px;
    top: 50%;
    transform: translateY(-50%);
    z-index: 200;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .step {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    padding: 9px 0;
    background: none;
    border: none;
    cursor: pointer;
    -webkit-tap-highlight-color: transparent;
  }

  .dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: var(--border);
    transition: width 0.35s cubic-bezier(0.4, 0, 0.2, 1),
      height 0.35s cubic-bezier(0.4, 0, 0.2, 1),
      background 0.35s ease, box-shadow 0.35s ease;
  }

  .step.active .dot {
    width: 10px;
    height: 10px;
    background: var(--primary-dark);
    box-shadow: 0 0 0 5px var(--primary-soft);
  }

  .connector {
    width: 2px;
    height: 26px;
    border-radius: 1px;
    background: var(--border);
    overflow: hidden;
  }

  .connector-fill {
    width: 100%;
    height: 0%;
    background: var(--primary-dark);
    transition: height 0.45s cubic-bezier(0.4, 0, 0.2, 1);
  }

  .label {
    position: absolute;
    right: 22px;
    top: 50%;
    transform: translate(6px, -50%);
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 0.6px;
    text-transform: uppercase;
    color: var(--text);
    white-space: nowrap;
    background: var(--background);
    padding: 4px 10px;
    border-radius: 6px;
    border: 1px solid var(--border);
    box-shadow: 0 8px 30px rgba(15, 23, 42, 0.06);
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.25s ease, transform 0.25s ease;
  }

  .step.active .label,
  .step:hover .label {
    opacity: 1;
    transform: translate(0, -50%);
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
      <span class="label">{step.label}</span>
    </button>
    {#if i < steps.length - 1}
      <span class="connector">
        <span class="connector-fill" style="height: {i < activeIndex ? '100%' : '0%'}"></span>
      </span>
    {/if}
  {/each}
</nav>

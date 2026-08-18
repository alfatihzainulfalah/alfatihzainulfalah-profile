<script>
  import { createEventDispatcher } from 'svelte';
  import CardProject from './CardProject.svelte';

  export let projects = [];

  const dispatch = createEventDispatcher();

  let viewport;
  let currentIndex = 0;
  let scrollRaf = null;

  function reduceMotion() {
    return window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  }

  function goTo(index) {
    const clamped = Math.max(0, Math.min(index, projects.length - 1));
    currentIndex = clamped;
    if (!viewport) return;
    viewport.scrollTo({
      left: clamped * viewport.clientWidth,
      behavior: reduceMotion() ? 'auto' : 'smooth'
    });
  }

  function prev() {
    goTo(currentIndex - 1);
  }

  function next() {
    goTo(currentIndex + 1);
  }

  function handleScroll() {
    if (scrollRaf) return;
    scrollRaf = requestAnimationFrame(() => {
      if (viewport) {
        const width = viewport.clientWidth || 1;
        currentIndex = Math.round(viewport.scrollLeft / width);
      }
      scrollRaf = null;
    });
  }

  function handleKeydown(event) {
    if (event.key === 'ArrowLeft') {
      event.preventDefault();
      prev();
    } else if (event.key === 'ArrowRight') {
      event.preventDefault();
      next();
    }
  }
</script>

<style>
  .carousel {
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .carousel-viewport {
    width: 100%;
    overflow-x: auto;
    overflow-y: hidden;
    scroll-snap-type: x mandatory;
    -webkit-overflow-scrolling: touch;
    scrollbar-width: none;
    border-radius: 14px;
  }

  .carousel-viewport::-webkit-scrollbar {
    display: none;
  }

  .carousel-viewport:focus-visible {
    outline: 2px solid var(--primary);
    outline-offset: 3px;
  }

  .carousel-track {
    display: flex;
  }

  .carousel-slide {
    flex: 0 0 100%;
    width: 100%;
    box-sizing: border-box;
    scroll-snap-align: start;
  }

  .carousel-controls {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 14px;
  }

  .carousel-btn {
    flex-shrink: 0;
    width: 36px;
    height: 36px;
    border-radius: 10px;
    border: 1px solid var(--border);
    background: var(--background);
    color: var(--text);
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: background 0.2s ease, color 0.2s ease, border-color 0.2s ease;
  }

  .carousel-btn:hover:not(:disabled) {
    background: var(--primary-soft);
    color: var(--primary-dark);
    border-color: var(--primary);
  }

  .carousel-btn:focus-visible {
    outline: 2px solid var(--primary);
    outline-offset: 2px;
  }

  .carousel-btn:disabled {
    opacity: 0.35;
    cursor: default;
  }

  .carousel-dots {
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .dot-btn {
    padding: 6px;
    background: none;
    border: none;
    cursor: pointer;
    -webkit-tap-highlight-color: transparent;
  }

  .dot-btn:focus-visible {
    outline: 2px solid var(--primary);
    outline-offset: 2px;
    border-radius: 4px;
  }

  .dot {
    display: block;
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: var(--border);
    transition: width 0.25s ease, height 0.25s ease, background 0.25s ease, box-shadow 0.25s ease;
  }

  .dot-btn.active .dot {
    width: 10px;
    height: 10px;
    background: var(--primary-dark);
    box-shadow: 0 0 0 4px var(--primary-soft);
  }

  @media (prefers-reduced-motion: reduce) {
    .carousel-btn,
    .dot {
      transition: none;
    }
  }
</style>

<div class="carousel" role="region" aria-label="Projects">
  <div
    class="carousel-viewport"
    bind:this={viewport}
    on:scroll={handleScroll}
    on:keydown={handleKeydown}
    tabindex="0"
  >
    <div class="carousel-track">
      {#each projects as project}
        <div class="carousel-slide">
          <CardProject {project} on:select={(event) => dispatch('select', event.detail)} />
        </div>
      {/each}
    </div>
  </div>

  {#if projects.length > 1}
    <div class="carousel-controls">
      <button
        type="button"
        class="carousel-btn"
        on:click={prev}
        disabled={currentIndex === 0}
        aria-label="Previous project"
      >
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><polyline points="15 18 9 12 15 6" /></svg>
      </button>

      <div class="carousel-dots">
        {#each projects as project, i}
          <button
            type="button"
            class="dot-btn"
            class:active={i === currentIndex}
            on:click={() => goTo(i)}
            aria-label={`Go to ${project.name}`}
            aria-current={i === currentIndex ? 'true' : undefined}
          >
            <span class="dot"></span>
          </button>
        {/each}
      </div>

      <button
        type="button"
        class="carousel-btn"
        on:click={next}
        disabled={currentIndex === projects.length - 1}
        aria-label="Next project"
      >
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><polyline points="9 18 15 12 9 6" /></svg>
      </button>
    </div>
  {/if}
</div>

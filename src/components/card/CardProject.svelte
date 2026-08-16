<script>
  import { createEventDispatcher } from 'svelte';

  export let project;

  const dispatch = createEventDispatcher();

  function handleClick() {
    dispatch('select', project);
  }

  function handleKeydown(event) {
    if (event.key === 'Enter' || event.key === ' ') {
      event.preventDefault();
      handleClick();
    }
  }
</script>

<style>
  .card {
    width: 100%;
    height: 100%;
    cursor: pointer;
    background: var(--background);
    border: 1px solid var(--border);
    border-radius: 14px;
    box-shadow: 0 8px 30px rgba(15, 23, 42, 0.06);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    padding: 18px;
    transition: transform 0.2s ease, box-shadow 0.2s ease, border-color 0.2s ease;
  }

  .card:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 32px rgba(15, 23, 42, 0.1);
    border-color: var(--primary);
  }

  .card:focus-visible {
    outline: 2px solid var(--primary);
    outline-offset: 3px;
  }

  .card-title {
    font-weight: 600;
    font-size: 14px;
    color: var(--text);
    margin-bottom: 8px;
  }

  .card-desc {
    font-size: 12px;
    color: var(--text-muted);
    line-height: 1.5;
  }

  .card-accent {
    margin-top: auto;
    width: 100%;
    height: 48px;
    border-radius: 8px;
  }

  @media (prefers-reduced-motion: reduce) {
    .card {
      transition: none;
    }

    .card:hover {
      transform: none;
    }
  }
</style>

<div
  class="card"
  role="button"
  tabindex="0"
  on:click={handleClick}
  on:keydown={handleKeydown}
>
  <div class="card-title">{project.name}</div>
  <div class="card-desc">{project.desc}</div>
  <div class="card-accent" style="background: linear-gradient(90deg, {project.color1}20 0%, {project.color2}20 100%);"></div>
</div>

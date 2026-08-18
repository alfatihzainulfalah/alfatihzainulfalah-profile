<script>
  import { createEventDispatcher } from 'svelte';
  import logoProfile from '../../assets/logo-profile.webp';

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
    position: relative;
    width: 100%;
    height: 100%;
    cursor: pointer;
    background: linear-gradient(180deg, var(--background) 0%, var(--surface) 100%);
    border: 1px solid var(--border);
    border-radius: 14px;
    box-shadow: 0 8px 30px rgba(15, 23, 42, 0.06);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    padding: 18px;
    transition: transform 0.2s ease, box-shadow 0.2s ease, border-color 0.2s ease;
  }

  .card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--primary) 0%, var(--primary-dark) 100%);
    opacity: 0;
    transition: opacity 0.2s ease;
    z-index: 2;
  }

  .card:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 32px rgba(15, 23, 42, 0.1);
    border-color: var(--primary);
  }

  .card:hover::before {
    opacity: 1;
  }

  .card:focus-visible {
    outline: 2px solid var(--primary);
    outline-offset: 3px;
  }

  .card-watermark {
    position: absolute;
    right: -18px;
    bottom: -18px;
    width: 96px;
    height: 96px;
    background-image: var(--watermark-src);
    background-size: contain;
    background-repeat: no-repeat;
    opacity: 0.07;
    transition: opacity 0.2s ease;
    z-index: 0;
    pointer-events: none;
  }

  .card:hover .card-watermark {
    opacity: 0.12;
  }

  .card-content {
    position: relative;
    z-index: 1;
    flex: 1;
    min-height: 0;
    display: flex;
    flex-direction: column;
  }

  .card-media {
    width: 100%;
    aspect-ratio: 4 / 3;
    border-radius: 8px;
    overflow: hidden;
    margin-bottom: 12px;
    background: var(--surface);
    border: 1px solid var(--border);
  }

  .card-media img {
    display: block;
    width: 100%;
    height: 100%;
    object-fit: cover;
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

    .card::before,
    .card-watermark {
      transition: none;
    }
  }
</style>

<div
  class="card"
  role="button"
  tabindex="0"
  on:click={handleClick}
  on:keydown={handleKeydown}
  style="--watermark-src: url({logoProfile});"
>
  <div class="card-watermark" aria-hidden="true"></div>
  <div class="card-content">
    {#if project.image}
      <div class="card-media">
        <img src={project.image} alt="{project.name} preview" loading="lazy" decoding="async" />
      </div>
    {/if}
    <div class="card-title">{project.name}</div>
    <div class="card-desc">{project.desc}</div>
    {#if !project.image}
      <div class="card-accent" style="background: linear-gradient(90deg, {project.color1}20 0%, {project.color2}20 100%);"></div>
    {/if}
  </div>
</div>

<script>
  import { createEventDispatcher } from 'svelte';
  import { fade, scale } from 'svelte/transition';

  export let project;

  const dispatch = createEventDispatcher();

  function close() {
    dispatch('close');
  }

  function handleKeydown(event) {
    if (event.key === 'Escape') close();
  }
</script>

<svelte:window on:keydown={handleKeydown} />

<!-- svelte-ignore a11y_click_events_have_key_events -->
<!-- svelte-ignore a11y_no_static_element_interactions -->
<div
  class="backdrop"
  on:click={close}
  transition:fade={{ duration: 180 }}
>
  <!-- svelte-ignore a11y_click_events_have_key_events -->
  <!-- svelte-ignore a11y_no_static_element_interactions -->
  <div
    class="modal"
    role="dialog"
    aria-modal="true"
    aria-labelledby="project-modal-title"
    tabindex="-1"
    on:click|stopPropagation
    transition:scale={{ duration: 220, start: 0.9 }}
  >
    <button class="close-btn" on:click={close} aria-label="Close">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><line x1="18" y1="6" x2="6" y2="18" /><line x1="6" y1="6" x2="18" y2="18" /></svg>
    </button>

    <div class="banner" style="background: linear-gradient(135deg, {project.color1} 0%, {project.color2} 100%);"></div>

    <div class="content">
      <h2 id="project-modal-title" class="title">{project.name}</h2>
      <p class="desc">{project.desc}</p>
    </div>
  </div>
</div>

<style>
  .backdrop {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 100;
    padding: 20px;
    border: none;
  }

  .modal {
    width: 100%;
    max-width: 480px;
    background: var(--background);
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 20px 50px rgba(15, 23, 42, 0.18);
    position: relative;
  }

  .close-btn {
    position: absolute;
    top: 14px;
    right: 14px;
    width: 32px;
    height: 32px;
    border-radius: 8px;
    border: 1px solid var(--border);
    background: rgba(255, 255, 255, 0.9);
    color: var(--text-muted);
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    z-index: 1;
    transition: background 0.2s, color 0.2s, border-color 0.2s;
  }

  .close-btn:hover {
    background: var(--primary-soft);
    color: var(--primary-dark);
    border-color: var(--primary);
  }

  .close-btn:focus-visible {
    outline: 2px solid var(--primary);
    outline-offset: 2px;
  }

  .banner {
    width: 100%;
    height: 160px;
  }

  .content {
    padding: 28px;
  }

  .title {
    font-size: 22px;
    font-weight: 700;
    color: var(--text);
    margin-bottom: 10px;
  }

  .desc {
    font-size: 14px;
    line-height: 1.6;
    color: var(--text-muted);
  }
</style>

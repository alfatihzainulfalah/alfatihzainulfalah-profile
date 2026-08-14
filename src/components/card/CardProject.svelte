<script>
  import { createEventDispatcher } from 'svelte';

  export let project;

  const dispatch = createEventDispatcher();

  let isFlipping = false;

  function handleClick() {
    dispatch('select', project);
    if (isFlipping) return;
    isFlipping = true;
  }

  function handleKeydown(event) {
    if (event.key === 'Enter' || event.key === ' ') {
      event.preventDefault();
      handleClick();
    }
  }

  function handleAnimationEnd() {
    isFlipping = false;
  }
</script>

<style>
  @keyframes float1 { 0%, 100% { transform: translateY(0px) rotate(-6deg); } 50% { transform: translateY(-12px) rotate(-6deg); } }
  @keyframes float2 { 0%, 100% { transform: translateY(0px) rotate(4deg); } 50% { transform: translateY(-10px) rotate(4deg); } }
  @keyframes float3 { 0%, 100% { transform: translateY(0px) rotate(-5deg); } 50% { transform: translateY(-14px) rotate(-5deg); } }
  @keyframes float4 { 0%, 100% { transform: translateY(0px) rotate(6deg); } 50% { transform: translateY(-8px) rotate(6deg); } }
  @keyframes float5 { 0%, 100% { transform: translateY(0px) rotate(-4deg); } 50% { transform: translateY(-11px) rotate(-4deg); } }
  @keyframes float6 { 0%, 100% { transform: translateY(0px) rotate(5deg); } 50% { transform: translateY(-9px) rotate(5deg); } }

  @keyframes cardFlip {
    0% { transform: rotateY(0deg) scale(1); }
    50% { transform: rotateY(180deg) scale(1.08); }
    100% { transform: rotateY(360deg) scale(1); }
  }

  .card {
    position: absolute;
    width: 280px;
    height: 200px;
    perspective: 800px;
    cursor: pointer;
  }

  .card:focus-visible {
    outline: 2px solid rgba(59, 130, 246, 0.6);
    outline-offset: 4px;
    border-radius: 12px;
  }

  .card-inner {
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, #f5f5f5 0%, #ffffff 100%);
    border-radius: 12px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.08);
    border: 1px solid rgba(0, 0, 0, 0.05);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    padding: 20px;
    transform-style: preserve-3d;
    backface-visibility: hidden;
    transition: box-shadow 0.3s ease;
  }

  .card-inner.flipping {
    animation: cardFlip 0.6s cubic-bezier(0.45, 0, 0.55, 1);
    box-shadow: 0 20px 45px rgba(0, 0, 0, 0.2);
  }

  .card-title {
    font-weight: 600;
    font-size: 14px;
    color: #1a1a1a;
    margin-bottom: 8px;
  }

  .card-desc {
    font-size: 12px;
    color: rgba(26, 26, 26, 0.6);
    line-height: 1.5;
  }

  .card-accent {
    margin-top: auto;
    width: 100%;
    height: 60px;
    border-radius: 8px;
  }

  .card:nth-child(1) { top: 60px; right: 100px; z-index: 30; animation: float1 4s ease-in-out infinite; }
  .card:nth-child(2) { top: 140px; right: 20px; z-index: 25; animation: float2 5s ease-in-out infinite; }
  .card:nth-child(3) { top: 320px; right: 140px; z-index: 20; animation: float3 4.5s ease-in-out infinite; }
  .card:nth-child(4) { bottom: 80px; right: 60px; z-index: 28; animation: float4 5.2s ease-in-out infinite; }
  .card:nth-child(5) { bottom: 120px; right: 280px; z-index: 22; animation: float5 4.8s ease-in-out infinite; }
  .card:nth-child(6) { top: 200px; left: 40px; z-index: 26; animation: float6 5.5s ease-in-out infinite; }

  @media (max-width: 768px) {
    .card {
      position: relative !important;
      top: auto !important;
      right: auto !important;
      bottom: auto !important;
      left: auto !important;
      z-index: auto !important;
      width: 100%;
      height: 140px;
      animation: none !important;
    }

    .card-inner {
      padding: 12px;
      box-shadow: 0 4px 16px rgba(0, 0, 0, 0.06);
      border-radius: 10px;
    }

    .card-accent {
      height: 32px;
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
  <div class="card-inner" class:flipping={isFlipping} on:animationend={handleAnimationEnd}>
    <div class="card-title">{project.name}</div>
    <div class="card-desc">{project.desc}</div>
    <div class="card-accent" style="background: linear-gradient(90deg, {project.color1}20 0%, {project.color2}20 100%);"></div>
  </div>
</div>

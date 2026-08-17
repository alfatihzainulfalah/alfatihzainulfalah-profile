<script>
  import { onMount } from 'svelte';
  import CardProject from './components/card/CardProject.svelte';
  import CardCertificate from './components/card/CardCertificate.svelte';
  import ProjectModal from './components/modal/ProjectModal.svelte';
  import StepIndicator from './components/StepIndicator.svelte';
  import akunterPreview from './assets/project-akunter.webp';
  import modifyAiPreview from './assets/project-modifyai.webp';

  let developerName = "Al Fatih\nZainul\nFalah";
  let subtitle = "Software Engineer & Creative Technologist";

  let typedSubtitle = '';
  let showCursor = true;

  onMount(() => {
    const reduceMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
    if (reduceMotion) {
      typedSubtitle = subtitle;
      showCursor = false;
      return;
    }

    let i = 0;
    const typeInterval = setInterval(() => {
      i += 1;
      typedSubtitle = subtitle.slice(0, i);
      if (i >= subtitle.length) {
        clearInterval(typeInterval);
        setTimeout(() => { showCursor = false; }, 1400);
      }
    }, 40);

    return () => clearInterval(typeInterval);
  });

  /** @type {{ name: string, desc: string, color1: string, color2: string, image?: string } | null} */
  let selectedProject = null;

  /** @param {CustomEvent} event */
  function openProject(event) {
    selectedProject = event.detail;
  }

  function closeProject() {
    selectedProject = null;
  }

  const projects = [
    { name: "Catering Application", desc: "Full-stack Catering application", color1: "rgb(59, 130, 246)", color2: "rgb(139, 92, 246)", image: akunterPreview },
    { name: "Cashier Application", desc: "Cashier Project", color1: "rgb(34, 197, 94)", color2: "rgb(59, 130, 246)", image: modifyAiPreview },
  ];

  const socials = [
    { name: "GitHub", url: "https://github.com", slug: "github", color: "181717" },
    { name: "Instagram", url: "https://instagram.com", slug: "instagram", color: "E4405F" },
    { name: "LinkedIn", url: "https://linkedin.com", slug: "linkedin", color: "0A66C2" },
    { name: "TikTok", url: "https://tiktok.com", slug: "tiktok", color: "000000" }
  ];

  const techLogos = [
    { name: "React", slug: "react", color: "61DAFB" },
    { name: "JavaScript", slug: "javascript", color: "F7DF1E" },
    { name: "Vue.js", slug: "vuedotjs", color: "4FC08D" },
    { name: "Laravel", slug: "laravel", color: "FF2D20" },
    { name: "PHP", slug: "php", color: "777BB4" },
    { name: "Express", slug: "express", color: "1a1a1a" },
    { name: "Linux", slug: "linux", color: "FCC624" },
    { name: "Kali Linux", slug: "kalilinux", color: "557C94" },
    { name: "Arch Linux", slug: "archlinux", color: "1793D1" },
    { name: "GitHub", slug: "github", color: "1a1a1a" },
    { name: "TypeScript", slug: "typescript", color: "3178C6" },
    { name: "Node.js", slug: "nodedotjs", color: "5FA04E" },
    { name: "HTML5", slug: "html5", color: "E34F26" },
    { name: "CSS3", slug: "css3", color: "1572B6" },
    { name: "Tailwind CSS", slug: "tailwindcss", color: "06B6D4" },
    { name: "Docker", slug: "docker", color: "2496ED" },
    { name: "Git", slug: "git", color: "F05032" },
    { name: "MySQL", slug: "mysql", color: "4479A1" },
    { name: "PostgreSQL", slug: "postgresql", color: "4169E1" },
    { name: "MongoDB", slug: "mongodb", color: "47A248" },
    { name: "Figma", slug: "figma", color: "F24E1E" },
    { name: "Python", slug: "python", color: "3776AB" },
    { name: "Svelte", slug: "svelte", color: "FF3E00" },
    { name: "Vercel", slug: "vercel", color: "1a1a1a" }
  ];
  const carouselLogos = [...techLogos, ...techLogos];

  const aboutText = "I'm a software engineer who enjoys turning ideas into fast, well-crafted products. I work across the stack, from designing clean interfaces to building reliable APIs, and I care about the small details that make software feel effortless to use.";

  const aboutStats = [
    { value: "3+", label: "Years Experience" },
    { value: "20+", label: "Projects Completed" },
    { value: "10+", label: "Certifications" }
  ];

  const certificates = [
    { title: "Full-Stack Web Development", issuer: "Dicoding Indonesia", date: "2024", color1: "rgb(59, 130, 246)", color2: "rgb(139, 92, 246)" },
    { title: "React - The Complete Guide", issuer: "Udemy", date: "2023", color1: "rgb(34, 197, 94)", color2: "rgb(59, 130, 246)" },
    { title: "AWS Cloud Practitioner", issuer: "Amazon Web Services", date: "2024", color1: "rgb(245, 158, 11)", color2: "rgb(239, 68, 68)" },
    { title: "Advanced JavaScript Concepts", issuer: "freeCodeCamp", date: "2023", color1: "rgb(168, 85, 247)", color2: "rgb(236, 72, 153)" },
    { title: "UI/UX Design Fundamentals", issuer: "Google", date: "2023", color1: "rgb(34, 197, 94)", color2: "rgb(168, 85, 247)" },
    { title: "Database Design & SQL", issuer: "Coursera", date: "2022", color1: "rgb(59, 130, 246)", color2: "rgb(14, 165, 233)" }
  ];

  const sections = [
    { id: "home", label: "Home" },
    { id: "about", label: "About" },
    { id: "certificates", label: "Certificates" }
  ];
</script>

<style>
  :global(:root) {
    --primary: #38bdf8;
    --primary-dark: #0284c7;
    --primary-soft: #e0f2fe;
    --primary-pale: #f0f9ff;
    --background: #ffffff;
    --surface: #f8fafc;
    --text: #111827;
    --text-muted: #64748b;
    --border: #e2e8f0;
    --font-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  }

  :global(*) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  :global(body) {
    font-family: var(--font-sans);
    background: var(--background);
    overflow-x: hidden;
  }

  .container {
    display: flex;
    height: 100vh;
    width: 100%;
    position: relative;
    overflow: hidden;
  }

  .left-section {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    padding: 80px 60px;
    position: relative;
    z-index: 10;
  }

  .name-box {
    max-width: 500px;
  }

  .name {
    font-size: 64px;
    font-weight: 800;
    line-height: 1.08;
    margin-bottom: 14px;
    color: var(--text);
    letter-spacing: -1.5px;
    white-space: pre-line;
  }

  .subtitle {
    font-size: 18px;
    color: var(--text-muted);
    font-weight: 500;
    letter-spacing: 0.5px;
    min-height: 1.4em;
  }

  .sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
  }

  .cursor {
    display: inline-block;
    width: 2px;
    height: 1em;
    margin-left: 2px;
    background: var(--primary);
    vertical-align: -0.15em;
    animation: blink 1s step-end infinite;
  }

  .cursor.hidden {
    opacity: 0;
    animation: none;
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  @media (prefers-reduced-motion: reduce) {
    .cursor {
      animation: none;
      opacity: 0;
    }
  }

  .divider {
    width: 40px;
    height: 2px;
    background: var(--primary);
    border-radius: 2px;
    margin-top: 24px;
    margin-bottom: 20px;
  }

  .socials {
    display: flex;
    gap: 16px;
    align-items: center;
    justify-content: center;
  }

  .social-icon {
    width: 32px;
    height: 32px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    text-decoration: none;
    transition: background 0.2s, border-color 0.2s, color 0.2s;
    color: var(--text-muted);
    cursor: pointer;
  }

  .social-icon:hover {
    background: var(--primary-soft);
    border-color: var(--primary);
    color: var(--primary-dark);
  }

  .social-icon:focus-visible {
    outline: 2px solid var(--primary);
    outline-offset: 2px;
  }

  .social-icon img {
    width: 16px;
    height: 16px;
    object-fit: contain;
  }

  .site-footer {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
    padding: 40px 60px;
    border-top: 1px solid var(--border);
  }

  .footer-text {
    font-size: 13px;
    color: var(--text-muted);
  }

  @keyframes scroll-logos {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }

  .logo-carousel {
    margin-top: 36px;
    width: 100%;
    max-width: 420px;
    position: relative;
    overflow: hidden;
    -webkit-mask-image: linear-gradient(90deg, transparent 0%, #000 12%, #000 88%, transparent 100%);
    mask-image: linear-gradient(90deg, transparent 0%, #000 12%, #000 88%, transparent 100%);
  }

  .logo-track {
    display: flex;
    align-items: center;
    gap: 32px;
    width: max-content;
    animation: scroll-logos 24s linear infinite;
  }

  .logo-carousel:hover .logo-track {
    animation-play-state: paused;
  }

  @media (prefers-reduced-motion: reduce) {
    .logo-track {
      animation: none;
    }
  }

  .logo-item {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 36px;
    height: 36px;
    flex-shrink: 0;
    opacity: 0.75;
    transition: opacity 0.2s, transform 0.2s;
  }

  .logo-item:hover {
    opacity: 1;
    transform: translateY(-2px);
  }

  .logo-item img {
    width: 28px;
    height: 28px;
    object-fit: contain;
  }

  .right-section {
    flex: 1;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 40px;
    background: var(--surface);
  }

  .grid-bg {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    opacity: 0.8;
    pointer-events: none;
  }

  .cards-container {
    position: relative;
    z-index: 2;
    width: 100%;
    max-width: 560px;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 16px;
  }

  .section-label {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 16px;
  }

  .label-index {
    font-size: 13px;
    font-weight: 700;
    color: var(--primary-dark);
    font-variant-numeric: tabular-nums;
  }

  .label-line {
    width: 28px;
    height: 1px;
    background: var(--border);
  }

  .label-text {
    font-size: 13px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1.5px;
    color: var(--text-muted);
  }

  .about-section {
    padding: 120px 60px;
    max-width: 1200px;
    margin: 0 auto;
  }

  .section-title {
    font-size: 40px;
    font-weight: 800;
    color: var(--text);
    letter-spacing: -1px;
    margin-bottom: 24px;
    max-width: 620px;
  }

  .about-text {
    font-size: 16px;
    line-height: 1.8;
    color: var(--text-muted);
    max-width: 640px;
    margin-bottom: 48px;
  }

  .about-stats {
    display: flex;
    gap: 48px;
    flex-wrap: wrap;
  }

  .stat-item {
    display: flex;
    flex-direction: column;
    gap: 4px;
    padding-left: 20px;
    border-left: 2px solid var(--primary);
  }

  .stat-value {
    font-size: 32px;
    font-weight: 800;
    color: var(--text);
    letter-spacing: -0.5px;
  }

  .stat-label {
    font-size: 13px;
    color: var(--text-muted);
    font-weight: 500;
  }

  .certificates-section {
    padding: 40px 60px 140px;
    max-width: 1200px;
    margin: 0 auto;
  }

  .certificates-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 24px;
    margin-top: 48px;
  }

  @media (max-width: 900px) {
    .certificates-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (max-width: 768px) {
    .container {
      flex-direction: column;
    }

    .left-section {
      flex: none;
      padding: 32px 20px;
      justify-content: center;
      align-items: center;
      text-align: center;
    }

    .name {
      font-size: 32px;
      letter-spacing: -0.5px;
      white-space: normal;
    }

    .subtitle {
      font-size: 14px;
    }

    .name-box {
      width: 100%;
      max-width: 100%;
    }

    .divider {
      width: 30px;
      margin: 16px auto 0;
    }

    .right-section {
      padding: 20px;
      flex: none;
    }

    .cards-container {
      grid-template-columns: 1fr 1fr;
      gap: 12px;
      max-width: 100%;
    }

    .social-icon {
      width: 28px;
      height: 28px;
    }

    .logo-carousel {
      max-width: 100%;
      margin-top: 24px;
    }

    .site-footer {
      padding: 32px 20px;
    }

    .about-section {
      padding: 64px 20px;
    }

    .certificates-section {
      padding: 24px 20px 80px;
    }

    .section-title {
      font-size: 28px;
    }

    .about-stats {
      gap: 28px;
    }

    .certificates-grid {
      grid-template-columns: 1fr;
    }
  }
</style>

<div class="container" id="home">
  <div class="left-section">
    <div class="name-box">
      <h1 class="name">{developerName}</h1>
      <p class="subtitle">
        <span aria-hidden="true">{typedSubtitle}<span class="cursor" class:hidden={!showCursor}></span></span>
        <span class="sr-only">{subtitle}</span>
      </p>
      <div class="divider"></div>

      <div class="logo-carousel">
        <div class="logo-track">
          {#each carouselLogos as logo}
            <div class="logo-item" title={logo.name}>
              <img src={`https://cdn.simpleicons.org/${logo.slug}/${logo.color}`} alt={logo.name} loading="lazy" />
            </div>
          {/each}
        </div>
      </div>
    </div>
  </div>

  <div class="right-section">
    <svg class="grid-bg" preserveAspectRatio="none">
      <defs>
        <pattern id="dots" width="22" height="22" patternUnits="userSpaceOnUse">
          <circle cx="2" cy="2" r="1.5" fill="rgba(2, 132, 199, 0.16)" />
        </pattern>
      </defs>
      <rect width="100%" height="100%" fill="url(#dots)" />
    </svg>

    <div class="cards-container">
      {#each projects as project}
        <CardProject {project} on:select={openProject} />
      {/each}
    </div>
  </div>
</div>

<section id="about" class="about-section">
  <div class="section-label">
    <span class="label-index">01</span>
    <span class="label-line"></span>
    <span class="label-text">About</span>
  </div>
  <h2 class="section-title">A little about me</h2>
  <p class="about-text">{aboutText}</p>
  <div class="about-stats">
    {#each aboutStats as stat}
      <div class="stat-item">
        <span class="stat-value">{stat.value}</span>
        <span class="stat-label">{stat.label}</span>
      </div>
    {/each}
  </div>
</section>

<section id="certificates" class="certificates-section">
  <div class="section-label">
    <span class="label-index">02</span>
    <span class="label-line"></span>
    <span class="label-text">Certificates</span>
  </div>
  <h2 class="section-title">Certifications & achievements</h2>
  <div class="certificates-grid">
    {#each certificates as certificate}
      <CardCertificate {certificate} />
    {/each}
  </div>
</section>

<footer class="site-footer">
  <div class="socials">
    {#each socials as social}
      <a href={social.url} target="_blank" rel="noopener" class="social-icon" title={social.name}>
        {#if social.slug === "linkedin"}
          <svg width="16" height="16" viewBox="0 0 24 24" fill="#0A66C2" aria-hidden="true"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.475-2.236-1.986-2.236-1.081 0-1.722.722-2.004 1.418-.103.249-.129.597-.129.946v5.441h-3.554s.047-8.83 0-9.748h3.554v1.381c.472-.727 1.315-1.765 3.2-1.765 2.336 0 4.087 1.526 4.087 4.805v5.327zM5.337 9.433c-1.144 0-1.892-.762-1.892-1.72 0-.977.77-1.72 1.936-1.72 1.166 0 1.892.743 1.914 1.72 0 .958-.748 1.72-1.958 1.72zM3.56 20.452V10.704h3.554v9.748H3.56zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.225 0z"/></svg>
        {:else}
          <img src={`https://cdn.simpleicons.org/${social.slug}/${social.color}`} alt={social.name} width="16" height="16" loading="lazy" />
        {/if}
      </a>
    {/each}
  </div>
  <p class="footer-text">&copy; {new Date().getFullYear()} {developerName.replace(/\n/g, ' ')}</p>
</footer>

<StepIndicator steps={sections} />

{#if selectedProject}
  <ProjectModal project={selectedProject} on:close={closeProject} />
{/if}

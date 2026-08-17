<script>
  import CardProject from './src/components/card/CardProject.svelte';

  let developerName = "User Template";
  let subtitle = "Software Engineer & Creative Technologist";

  const projects = [
    { name: "Catering Application", desc: "Full-stack accounting application", color1: "rgb(59, 130, 246)", color2: "rgb(139, 92, 246)" },
    { name: "Cashier Application", desc: "AI-powered design tool", color1: "rgb(34, 197, 94)", color2: "rgb(59, 130, 246)" }
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
</script>

<style>
  :global(*) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  :global(body) {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    background: #ffffff;
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
    font-size: 96px;
    font-weight: 900;
    line-height: 1;
    margin-bottom: 12px;
    color: #1a1a1a;
    letter-spacing: -2px;
  }

  .subtitle {
    font-size: 18px;
    color: rgba(26, 26, 26, 0.6);
    font-weight: 500;
    letter-spacing: 0.5px;
  }

  .divider {
    width: 40px;
    height: 1px;
    background: rgba(26, 26, 26, 0.2);
    margin-top: 24px;
    margin-bottom: 20px;
  }

  .socials {
    display: flex;
    gap: 16px;
    align-items: center;
    margin-top: 28px;
  }

  .social-icon {
    width: 32px;
    height: 32px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: rgba(26, 26, 26, 0.05);
    border-radius: 8px;
    text-decoration: none;
    transition: all 0.2s;
    color: #1a1a1a;
    border: none;
    cursor: pointer;
  }

  .social-icon:hover {
    background: rgba(26, 26, 26, 0.15);
  }

  .social-icon img {
    width: 16px;
    height: 16px;
    object-fit: contain;
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
  }

  .grid-bg {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    opacity: 0.7;
  }

  .cards-container {
    position: relative;
    width: 100%;
    height: 100%;
    perspective: 1200px;
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
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
      max-height: 450px;
      overflow-y: auto;
      padding: 20px;
      flex: none;
      position: relative;
    }

    .cards-container {
      display: contents;
    }

    .socials {
      gap: 12px;
      justify-content: center;
    }

    .social-icon {
      width: 28px;
      height: 28px;
    }

    .logo-carousel {
      max-width: 100%;
      margin-top: 24px;
    }
  }
</style>

<div class="container">
  <div class="left-section">
    <div class="name-box">
      <h1 class="name">{developerName}</h1>
      <p class="subtitle">{subtitle}</p>
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

      <div class="socials">
        {#each socials as social}
          <a href={social.url} target="_blank" rel="noopener" class="social-icon" title={social.name}>
            <img src={`https://cdn.simpleicons.org/${social.slug}/${social.color}`} alt={social.name} width="16" height="16" loading="lazy" />
          </a>
        {/each}
      </div>
    </div>
  </div>

  <div class="right-section">
    <svg class="grid-bg" preserveAspectRatio="none">
      <defs>
        <pattern id="dots" width="22" height="22" patternUnits="userSpaceOnUse">
          <circle cx="2" cy="2" r="1.5" fill="rgba(26, 26, 26, 0.14)" />
        </pattern>
      </defs>
      <rect width="100%" height="100%" fill="url(#dots)" />
    </svg>

    <div class="cards-container">
      {#each projects as project}
        <CardProject {project} />
      {/each}
    </div>
  </div>
</div>

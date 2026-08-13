<script>
  let developerName = "Al Fatih Zainul Falah";
  let subtitle = "Software Engineer & Creative Technologist";

  const projects = [
    { name: "Akunter", desc: "Full-stack accounting application", color1: "rgb(59, 130, 246)", color2: "rgb(139, 92, 246)" },
    { name: "ModifyAI", desc: "AI-powered design tool", color1: "rgb(34, 197, 94)", color2: "rgb(59, 130, 246)" },
    { name: "TrendHub", desc: "Real-time analytics platform", color1: "rgb(168, 85, 247)", color2: "rgb(236, 72, 153)" },
    { name: "CloudSync", desc: "Cloud storage solution", color1: "rgb(59, 130, 246)", color2: "rgb(14, 165, 233)" },
    { name: "DataViz", desc: "Advanced data visualization", color1: "rgb(245, 158, 11)", color2: "rgb(239, 68, 68)" },
    { name: "MobileFirst", desc: "Progressive mobile app", color1: "rgb(34, 197, 94)", color2: "rgb(168, 85, 247)" }
  ];

  const socials = [
    { name: "GitHub", url: "https://github.com", icon: "github" },
    { name: "Instagram", url: "https://instagram.com", icon: "instagram" },
    { name: "LinkedIn", url: "https://linkedin.com", icon: "linkedin" },
    { name: "TikTok", url: "https://tiktok.com", icon: "tiktok" }
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
  @keyframes float1 { 0%, 100% { transform: translateY(0px) rotate(-6deg); } 50% { transform: translateY(-12px) rotate(-6deg); } }
  @keyframes float2 { 0%, 100% { transform: translateY(0px) rotate(4deg); } 50% { transform: translateY(-10px) rotate(4deg); } }
  @keyframes float3 { 0%, 100% { transform: translateY(0px) rotate(-5deg); } 50% { transform: translateY(-14px) rotate(-5deg); } }
  @keyframes float4 { 0%, 100% { transform: translateY(0px) rotate(6deg); } 50% { transform: translateY(-8px) rotate(6deg); } }
  @keyframes float5 { 0%, 100% { transform: translateY(0px) rotate(-4deg); } 50% { transform: translateY(-11px) rotate(-4deg); } }
  @keyframes float6 { 0%, 100% { transform: translateY(0px) rotate(5deg); } 50% { transform: translateY(-9px) rotate(5deg); } }

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

  .card {
    position: absolute;
    width: 280px;
    height: 200px;
    background: linear-gradient(135deg, #f5f5f5 0%, #ffffff 100%);
    border-radius: 12px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.08);
    border: 1px solid rgba(0, 0, 0, 0.05);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    padding: 20px;
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
      padding: 12px;
      box-shadow: 0 4px 16px rgba(0, 0, 0, 0.06);
      border-radius: 10px;
    }

    .card-accent {
      height: 32px;
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
      <div class="socials">
        {#each socials as social}
          <a href={social.url} target="_blank" rel="noopener" class="social-icon" title={social.name}>
            {#if social.icon === "github"}
              <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v 3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
            {:else if social.icon === "instagram"}
              <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069z"/></svg>
            {:else if social.icon === "linkedin"}
              <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.475-2.236-1.986-2.236-1.081 0-1.722.722-2.004 1.418-.103.249-.129.597-.129.946v5.441h-3.554s.05-8.81 0-9.728h3.554v1.375c.43-.664 1.199-1.61 2.92-1.61 2.135 0 3.732 1.39 3.732 4.377v5.586zM5.337 8.855c-1.144 0-1.915-.758-1.915-1.704 0-.948.77-1.704 1.963-1.704 1.192 0 1.912.756 1.938 1.704 0 .946-.746 1.704-1.938 1.704zm-1.6 11.597h3.19V9.24H3.737v11.212zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.225 0z"/></svg>
            {:else if social.icon === "tiktok"}
              <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M19.498 3.094c1.871.855 3.381 2.366 4.236 4.236.859 1.877.859 5.148 0 7.025-.855 1.87-2.365 3.381-4.236 4.236-1.877.859-5.148.859-7.025 0-1.87-.855-3.381-2.366-4.236-4.236-.859-1.877-.859-5.148 0-7.025.855-1.87 2.366-3.381 4.236-4.236 1.877-.859 5.148-.859 7.025 0z"/></svg>
            {/if}
          </a>
        {/each}
      </div>

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
          <circle cx="2" cy="2" r="1.5" fill="rgba(26, 26, 26, 0.14)" />
        </pattern>
      </defs>
      <rect width="100%" height="100%" fill="url(#dots)" />
    </svg>

    <div class="cards-container">
      {#each projects as project, i}
        <div class="card">
          <div class="card-title">{project.name}</div>
          <div class="card-desc">{project.desc}</div>
          <div class="card-accent" style="background: linear-gradient(90deg, {project.color1}20 0%, {project.color2}20 100%);"></div>
        </div>
      {/each}
    </div>
  </div>
</div>

<script>
  export let certificate;
</script>

<style>
  .cert-card {
    background: var(--background);
    border-radius: 14px;
    border: 1px solid var(--border);
    box-shadow: 0 8px 30px rgba(15, 23, 42, 0.06);
    padding: 24px;
    display: flex;
    flex-direction: column;
    gap: 10px;
    transition: transform 0.2s ease, box-shadow 0.2s ease, border-color 0.2s ease;
  }

  .cert-card:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 32px rgba(15, 23, 42, 0.1);
    border-color: var(--primary);
  }

  @media (prefers-reduced-motion: reduce) {
    .cert-card {
      transition: none;
    }

    .cert-card:hover {
      transform: none;
    }
  }

  .cert-icon {
    width: 44px;
    height: 44px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #ffffff;
    margin-bottom: 4px;
  }

  .cert-title {
    font-weight: 600;
    font-size: 15px;
    color: var(--text);
    line-height: 1.4;
  }

  .cert-issuer {
    font-size: 12px;
    color: var(--text-muted);
  }

  .cert-date {
    font-size: 11px;
    color: var(--text-muted);
    font-weight: 600;
    letter-spacing: 0.5px;
    text-transform: uppercase;
    margin-top: auto;
    padding-top: 6px;
  }

  .cert-bar {
    height: 4px;
    width: 100%;
    border-radius: 4px;
  }
</style>

<div class="cert-card">
  <div class="cert-icon" style="background: linear-gradient(135deg, {certificate.color1} 0%, {certificate.color2} 100%);">
    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
      <circle cx="12" cy="8" r="7" />
      <polyline points="8.21 13.89 7 23 12 20 17 23 15.79 13.88" />
    </svg>
  </div>
  <div class="cert-title">{certificate.title}</div>
  <div class="cert-issuer">{certificate.issuer}</div>
  <div class="cert-date">{certificate.date}</div>
  <div class="cert-bar" style="background: linear-gradient(90deg, {certificate.color1} 0%, {certificate.color2} 100%);"></div>
</div>

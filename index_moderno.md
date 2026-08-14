---
layout: style-index
---

<style>
:root {
  --bg: #f6f7fb;
  --surface: rgba(255,255,255,.86);
  --text: #172033;
  --muted: #687386;
  --accent: #7057d9;
  --accent-dark: #5139b8;
  --border: #e5e8f0;
  --shadow: 0 18px 45px rgba(35, 42, 70, .10);
}

body {
  background:
    radial-gradient(circle at 0 0, rgba(112,87,217,.14), transparent 30rem),
    var(--bg);
  color: var(--text);
}

.modern-page {
  max-width: 1080px;
  margin: 0 auto;
  padding: 28px 20px 48px;
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}

.modern-hero {
  position: relative;
  overflow: hidden;
  margin-bottom: 34px;
  padding: clamp(34px, 7vw, 78px) clamp(24px, 6vw, 70px);
  border-radius: 28px;
  color: white;
  background: linear-gradient(135deg, #201b48 0%, #5139b8 58%, #927de9 100%);
  box-shadow: var(--shadow);
}

.modern-hero::after {
  content: "";
  position: absolute;
  width: 260px;
  height: 260px;
  right: -80px;
  top: -90px;
  border: 1px solid rgba(255,255,255,.28);
  border-radius: 50%;
  box-shadow: 0 0 0 28px rgba(255,255,255,.05), 0 0 0 58px rgba(255,255,255,.04);
}

.modern-kicker {
  position: relative;
  z-index: 1;
  margin: 0 0 12px;
  color: #d8d0ff;
  font-size: .78rem;
  font-weight: 800;
  letter-spacing: .16em;
  text-transform: uppercase;
}

.modern-hero h1 {
  position: relative;
  z-index: 1;
  margin: 0;
  max-width: 700px;
  color: white;
  font-size: clamp(2.3rem, 7vw, 5.2rem);
  line-height: .98;
  letter-spacing: -.06em;
}

.modern-subtitle {
  position: relative;
  z-index: 1;
  margin: 20px 0 0;
  color: #eeeaff;
  font-size: clamp(1rem, 2vw, 1.18rem);
}

.modern-section-head {
  display: flex;
  align-items: end;
  justify-content: space-between;
  gap: 18px;
  margin: 0 0 16px;
}

.modern-section-head h2 {
  margin: 0;
  font-size: clamp(1.45rem, 3vw, 2rem);
  letter-spacing: -.035em;
}

.modern-count {
  margin: 0;
  color: var(--muted);
  font-size: .9rem;
}

.modern-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 14px;
  padding: 0;
  list-style: none;
}

.modern-list li {
  margin: 0;
  padding: 0;
}

.modern-list a {
  display: flex;
  min-height: 108px;
  flex-direction: column;
  justify-content: space-between;
  gap: 18px;
  padding: 20px;
  border: 1px solid var(--border);
  border-radius: 18px;
  background: var(--surface);
  color: var(--text);
  text-decoration: none;
  box-shadow: 0 5px 18px rgba(35,42,70,.035);
  transition: transform .2s ease, border-color .2s ease, box-shadow .2s ease, color .2s ease;
}

.modern-list a:hover,
.modern-list a:focus-visible {
  transform: translateY(-4px);
  border-color: rgba(112,87,217,.45);
  color: var(--accent-dark);
  box-shadow: 0 14px 28px rgba(35,42,70,.12);
  outline: none;
}

.modern-title {
  font-size: 1.08rem;
  font-weight: 750;
  line-height: 1.25;
}

.modern-date {
  color: var(--muted);
  font-size: .82rem;
}

.modern-footer {
  margin-top: 46px;
  padding-top: 26px;
  border-top: 1px solid var(--border);
  text-align: center;
}

.modern-footer a {
  color: var(--accent-dark);
  font-size: .9rem;
  font-weight: 700;
  text-decoration: none;
}

.modern-footer a:hover { text-decoration: underline; }

@media (prefers-color-scheme: dark) {
  :root {
    --bg: #10121b;
    --surface: rgba(28,31,44,.88);
    --text: #f1f2f8;
    --muted: #a5acc0;
    --border: #303548;
    --shadow: 0 18px 45px rgba(0,0,0,.25);
  }
}
</style>

<div class="modern-page">
  <header class="modern-hero">
    <p class="modern-kicker">Textos para ler devagar</p>
    <h1>Queime depois de ler</h1>
    <p class="modern-subtitle">Leia por sua conta e risco.</p>
  </header>

  <main>
    <div class="modern-section-head">
      <h2>Índice</h2>
      <p class="modern-count">Textos, memórias e outras combustões</p>
    </div>

    <ul class="modern-list">
      {% assign textos = site.pages | sort: 'date' | reverse %}
      {% for texto in textos %}
        {% if texto.title and texto.url != page.url %}
          <li>
            <a href="{{ texto.url | relative_url }}">
              <span class="modern-title">{{ texto.title }}</span>
              {% if texto.date %}<time class="modern-date" datetime="{{ texto.date | date: '%Y-%m-%d' }}">{{ texto.date | date: '%d/%m/%Y' }}</time>{% endif %}
            </a>
          </li>
        {% endif %}
      {% endfor %}
    </ul>
  </main>

  <footer class="modern-footer">
    <a href="{{ 'https://joaquim-capitao.github.io/' | relative_url }}" title="Página Inicial">⌂ &nbsp; Início</a>
  </footer>
</div>

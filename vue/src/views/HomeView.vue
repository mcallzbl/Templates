<template>
  <div class="home">
    <section class="hero">
      <div class="hero-content">
        <h1 class="hero-title">{{ $t('home.title') }}</h1>
        <p class="hero-subtitle">{{ $t('home.subtitle') }}</p>

        <div class="features-grid">
          <div class="feature-card">
            <div class="feature-icon">🚀</div>
            <h3>{{ $t('home.features.fast.title') }}</h3>
            <p>{{ $t('home.features.fast.description') }}</p>
          </div>

          <div class="feature-card">
            <div class="feature-icon">⚡</div>
            <h3>{{ $t('home.features.modern.title') }}</h3>
            <p>{{ $t('home.features.modern.description') }}</p>
          </div>

          <div class="feature-card">
            <div class="feature-icon">🎨</div>
            <h3>{{ $t('home.features.beautiful.title') }}</h3>
            <p>{{ $t('home.features.beautiful.description') }}</p>
          </div>
        </div>

        <div class="cta-section">
          <router-link to="/about" class="cta-button">
            {{ $t('home.getStarted') }}
          </router-link>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
.home {
  min-height: 70vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem 0;
}

.hero {
  width: 100%;
  position: relative;
  border-radius: 32px;
  padding: clamp(2rem, 4vw, 3.5rem);
  background: var(--surface-1);
  border: 1px solid var(--border-soft);
  box-shadow: var(--shadow-soft);
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  width: 320px;
  height: 320px;
  right: -120px;
  top: -160px;
  background: radial-gradient(circle at 30% 30%, rgba(63, 159, 147, 0.35), transparent 70%);
  opacity: 0.9;
}

.hero::after {
  content: '';
  position: absolute;
  width: 360px;
  height: 360px;
  left: -180px;
  bottom: -220px;
  background: radial-gradient(circle at 30% 30%, rgba(242, 163, 92, 0.35), transparent 70%);
  opacity: 0.9;
}

.hero-content {
  display: grid;
  grid-template-columns: minmax(0, 1.1fr) minmax(0, 0.9fr);
  grid-template-areas:
    'title cards'
    'subtitle cards'
    'cta cards';
  align-items: start;
  gap: 1.5rem 3rem;
  position: relative;
  z-index: 1;
  animation: heroIn 0.8s ease-out;
}

.hero-title {
  grid-area: title;
  font-family: var(--font-serif);
  font-size: clamp(2.6rem, 4vw, 4.6rem);
  font-weight: 600;
  color: var(--ink-900);
  margin-bottom: 0.5rem;
  letter-spacing: -0.02em;
}

.hero-subtitle {
  grid-area: subtitle;
  font-size: 1.15rem;
  color: var(--ink-700);
  max-width: 34rem;
}

.features-grid {
  grid-area: cards;
  display: grid;
  gap: 1.2rem;
}

.feature-card {
  --lift: 0px;
  background: var(--surface-2);
  padding: 1.6rem;
  border-radius: 18px;
  border: 1px solid var(--border-soft);
  box-shadow: var(--shadow-card);
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  position: relative;
  overflow: hidden;
  transform: translateY(var(--lift));
}

.feature-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(120deg, rgba(255, 255, 255, 0.5), transparent 45%);
  opacity: 0;
  transition: opacity 0.25s ease;
}

.feature-card:hover {
  transform: translateY(calc(var(--lift) - 6px));
  box-shadow: 0 24px 40px rgba(28, 21, 14, 0.18);
}

.feature-card:hover::before {
  opacity: 1;
}

.feature-card:nth-child(2) {
  --lift: 10px;
}

.feature-card:nth-child(3) {
  --lift: 20px;
}

.feature-icon {
  width: 48px;
  height: 48px;
  border-radius: 14px;
  display: grid;
  place-items: center;
  font-size: 1.5rem;
  background: rgba(255, 255, 255, 0.85);
  border: 1px solid var(--border-soft);
  box-shadow: var(--ring);
  margin-bottom: 0.9rem;
}

.feature-card h3 {
  font-size: 1.1rem;
  color: var(--ink-900);
  margin-bottom: 0.4rem;
  font-weight: 600;
}

.feature-card p {
  color: var(--ink-700);
  opacity: 0.9;
  line-height: 1.6;
}

.cta-section {
  grid-area: cta;
  margin-top: 0.5rem;
}

.cta-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.95rem 2rem;
  background: linear-gradient(135deg, rgba(63, 159, 147, 0.95), rgba(112, 203, 192, 0.95));
  color: #0b2b28;
  text-decoration: none;
  border-radius: 999px;
  font-weight: 600;
  font-size: 1.05rem;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  box-shadow: 0 18px 30px rgba(63, 159, 147, 0.25);
}

.cta-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 22px 34px rgba(63, 159, 147, 0.35);
}

@keyframes heroIn {
  from {
    opacity: 0;
    transform: translateY(24px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 900px) {
  .hero-content {
    grid-template-columns: 1fr;
    grid-template-areas:
      'title'
      'subtitle'
      'cards'
      'cta';
  }

  .features-grid {
    grid-template-columns: 1fr;
  }

  .feature-card {
    --lift: 0px;
  }
}

@media (max-width: 700px) {
  .hero-title {
    font-size: clamp(2.2rem, 7vw, 3rem);
  }

  .hero-subtitle {
    font-size: 1.05rem;
  }

  .hero {
    padding: 2rem 1.5rem;
  }

  .feature-card {
    padding: 1.4rem;
  }
}
</style>

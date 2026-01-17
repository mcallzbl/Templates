<template>
  <div class="about">
    <div class="about-card">
      <span class="eyebrow">{{ $t('about.eyebrow') }}</span>
      <h1>{{ $t('common.about') }}</h1>
      <p class="lead">{{ $t('about.intro') }}</p>
      <div class="about-body">
        <p>{{ $t('about.story') }}</p>
        <p>{{ $t('about.mission') }}</p>
      </div>
      <ul class="about-list">
        <li>{{ $t('about.highlights.fast') }}</li>
        <li>{{ $t('about.highlights.modern') }}</li>
        <li>{{ $t('about.highlights.beautiful') }}</li>
      </ul>
      <p class="stack">{{ $t('about.stack') }}</p>
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
.about {
  min-height: 60vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.about-card {
  width: min(680px, 100%);
  padding: clamp(2rem, 4vw, 3rem);
  border-radius: 28px;
  background: var(--surface-1);
  border: 1px solid var(--border-soft);
  box-shadow: var(--shadow-card);
  text-align: left;
}

.eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.9rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--ink-500);
  margin-bottom: 0.75rem;
}

.about-card h1 {
  font-family: var(--font-serif);
  font-size: clamp(2rem, 3vw, 2.8rem);
  color: var(--ink-900);
  margin-bottom: 0.8rem;
}

.lead {
  color: var(--ink-700);
  font-size: 1.05rem;
  margin-bottom: 1.4rem;
}

.about-body {
  display: grid;
  gap: 0.9rem;
  color: var(--ink-700);
  margin-bottom: 1.5rem;
}

.about-list {
  list-style: none;
  display: grid;
  gap: 0.75rem;
  margin-bottom: 1.3rem;
  padding: 0;
}

.about-list li {
  padding: 0.65rem 0.9rem;
  border-radius: 14px;
  background: var(--surface-2);
  border: 1px solid var(--border-soft);
  color: var(--ink-700);
  font-weight: 600;
}

.stack {
  color: var(--ink-500);
  font-size: 0.98rem;
}
</style>

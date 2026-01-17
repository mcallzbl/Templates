<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { useI18n } from 'vue-i18n'

const { locale } = useI18n()

const switchLanguage = () => {
  locale.value = locale.value === 'zh' ? 'en' : 'zh'
}
</script>

<template>
  <div class="app-shell">
    <header class="site-header">
      <div class="brand">
        <div class="logo-shell">
          <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="44" height="44" />
        </div>
      </div>

      <div class="nav-actions">
        <nav>
          <RouterLink to="/">{{ $t('navigation.home') }}</RouterLink>
          <RouterLink to="/about">{{ $t('navigation.about') }}</RouterLink>
        </nav>

        <button @click="switchLanguage" class="language-switch" type="button">
          {{ locale === 'zh' ? 'EN' : '中文' }}
        </button>
      </div>
    </header>

    <main class="app-main">
      <RouterView />
    </main>
  </div>
</template>

<style scoped>
.app-shell {
  width: min(1200px, 100%);
  display: flex;
  flex-direction: column;
  gap: clamp(1.5rem, 3vw, 2.5rem);
}

.site-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1.5rem;
  padding: 0.85rem 1rem;
  border-radius: 20px;
  background: var(--surface-1);
  border: 1px solid var(--border-soft);
  box-shadow: var(--shadow-card);
  backdrop-filter: blur(12px);
  position: relative;
  overflow: hidden;
}

.site-header::after {
  content: '';
  position: absolute;
  inset: auto 1.5rem 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, rgba(63, 159, 147, 0.6), transparent);
  opacity: 0.7;
}

.brand {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.logo-shell {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  padding: 6px;
  background: conic-gradient(from 130deg, var(--accent-1), var(--accent-2), var(--accent-3), var(--accent-1));
  box-shadow: var(--ring);
  display: grid;
  place-items: center;
}

.logo {
  width: 100%;
  height: 100%;
  filter: drop-shadow(0 6px 10px rgba(32, 20, 12, 0.2));
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  flex-wrap: wrap;
  justify-content: flex-end;
}

nav {
  display: flex;
  align-items: center;
  gap: 0.35rem;
  padding: 0.3rem;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.7);
  border: 1px solid var(--border-soft);
  box-shadow: var(--ring);
}

nav a {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.45rem 1rem;
  border-radius: 999px;
  text-decoration: none;
  font-weight: 600;
  color: var(--ink-700);
  transition: transform 0.2s ease, background 0.2s ease, color 0.2s ease;
}

nav a:hover {
  transform: translateY(-1px);
  background: rgba(255, 255, 255, 0.85);
  color: var(--ink-900);
}

nav a.router-link-active {
  background: linear-gradient(135deg, rgba(63, 159, 147, 0.9), rgba(112, 203, 192, 0.9));
  color: #0b2b28;
  box-shadow: 0 10px 20px rgba(63, 159, 147, 0.2);
}

.language-switch {
  padding: 0.5rem 0.9rem;
  border-radius: 999px;
  border: 1px solid var(--border-soft);
  background: linear-gradient(135deg, rgba(242, 163, 92, 0.95), rgba(217, 122, 94, 0.9));
  color: #2e1e13;
  font-weight: 600;
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  box-shadow: 0 12px 20px rgba(242, 163, 92, 0.25);
}

.language-switch:hover {
  transform: translateY(-1px);
  box-shadow: 0 16px 24px rgba(242, 163, 92, 0.3);
}

.app-main {
  flex: 1;
}

@media (max-width: 900px) {
  .site-header {
    align-items: flex-start;
    flex-direction: column;
  }

  .nav-actions {
    width: 100%;
    justify-content: space-between;
  }

  nav {
    flex: 1;
    justify-content: center;
  }
}

@media (max-width: 600px) {
  .nav-actions {
    gap: 0.6rem;
  }

  nav {
    flex-wrap: wrap;
  }

  .language-switch {
    width: 100%;
    justify-content: center;
  }
}
</style>

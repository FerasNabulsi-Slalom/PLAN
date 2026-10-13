<script setup lang="ts">
import { ref } from 'vue'

const isDark = ref(true)

const links = [
  {
    label: 'Portfolio',
    detail: 'Selected work and projects',
    href: 'https://your-portfolio-url.com',
    icon: 'portfolio',
    external: true,
  },
  {
    label: 'Dribbble',
    detail: 'Design shots and experiments',
    href: 'https://dribbble.com/',
    icon: 'dribbble',
    external: true,
  },
  {
    label: 'LinkedIn',
    detail: 'Professional updates',
    href: 'http://www.LinkedIn.com/in/FerasNabulsi',
    icon: 'linkedin',
    external: true,
  },
  {
    label: 'Email',
    detail: 'Let’s start a conversation',
    href: 'mailto:feras.nabulsi@slalom.com',
    icon: 'email',
    external: false,
  },
]

function toggleTheme() {
  isDark.value = !isDark.value
  document.documentElement.dataset.theme = isDark.value ? 'dark' : 'light'
}
</script>

<template>
  <main class="page-shell">
    <div class="ambient ambient-one" aria-hidden="true"></div>
    <div class="ambient ambient-two" aria-hidden="true"></div>

    <section class="profile-card" aria-labelledby="profile-name">
      <div class="card-topline">
        <span class="eyebrow"><span class="status-dot"></span> FIND ME ONLINE</span>
        <button
          class="theme-toggle"
          type="button"
          :aria-label="isDark ? 'Switch to light mode' : 'Switch to dark mode'"
          :aria-pressed="isDark"
          @click="toggleTheme"
        >
          <svg
            v-if="isDark"
            aria-hidden="true"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="1.7"
            stroke-linecap="round"
          >
            <circle cx="12" cy="12" r="3.8" />
            <path d="M12 2.5v2M12 19.5v2M4.9 4.9l1.4 1.4m11.4 11.4 1.4 1.4M2.5 12h2m15 0h2M4.9 19.1l1.4-1.4M17.7 6.3l1.4-1.4" />
          </svg>
          <svg
            v-else
            aria-hidden="true"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="1.7"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <path d="M20.2 15.2A8.4 8.4 0 0 1 8.8 3.8 8.5 8.5 0 1 0 20.2 15.2Z" />
          </svg>
          <span>{{ isDark ? 'Light' : 'Dark' }}</span>
        </button>
      </div>

      <header class="profile-header">
        <div class="avatar" role="img" aria-label="Profile photo placeholder">
          <span>FN</span>
          <span class="avatar-sparkle" aria-hidden="true">✳</span>
        </div>
        <h1 id="profile-name">Feras Nabulsi</h1>
        <p class="tagline">A little corner of the internet to explore my work and connect.</p>
      </header>

      <nav class="link-list" aria-label="My links">
        <a
          v-for="link in links"
          :key="link.label"
          class="link-card"
          :href="link.href"
          :target="link.external ? '_blank' : undefined"
          :rel="link.external ? 'noreferrer' : undefined"
        >
          <span class="link-icon" aria-hidden="true">
            <svg
              v-if="link.icon === 'portfolio'"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="1.6"
              stroke-linecap="round"
              stroke-linejoin="round"
            >
              <rect x="3.5" y="4" width="17" height="16" rx="2.5" />
              <path d="M8 8h3v3H8zM13 8h3M13 11h3M8 14h8M8 17h8" />
            </svg>
            <svg
              v-else-if="link.icon === 'dribbble'"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="1.55"
              stroke-linecap="round"
              stroke-linejoin="round"
            >
              <circle cx="12" cy="12" r="8.5" />
              <path d="M7.2 5.1c4.1 3.2 6.9 7.4 8.4 13.8M4 10.1c5.1.3 10.6-1.2 14.2-4.1M5.4 17.8c2.7-3.7 7.2-5.6 14.2-4.8" />
            </svg>
            <svg
              v-else-if="link.icon === 'linkedin'"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="1.7"
              stroke-linecap="round"
              stroke-linejoin="round"
            >
              <path d="M5 9v10M5 5.1v.1M10 19v-6a4 4 0 0 1 8 0v6M10 9v10" />
              <circle cx="5" cy="5" r=".7" fill="currentColor" stroke="none" />
            </svg>
            <svg
              v-else
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="1.6"
              stroke-linecap="round"
              stroke-linejoin="round"
            >
              <rect x="3.5" y="5" width="17" height="14" rx="2.5" />
              <path d="m4.5 7 7.5 6 7.5-6" />
            </svg>
          </span>
          <span class="link-copy">
            <span class="link-title">{{ link.label }}</span>
            <span class="link-detail">{{ link.detail }}</span>
          </span>
          <svg
            class="link-arrow"
            aria-hidden="true"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="1.7"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <path d="M5 12h14M13 6l6 6-6 6" />
          </svg>
        </a>
      </nav>

      <footer class="card-footer">
        <span class="footer-rule"></span>
        <span>Thanks for stopping by <span class="footer-star" aria-hidden="true">✳</span></span>
        <span class="footer-rule"></span>
      </footer>
    </section>

    <p class="page-credit">DESIGNED WITH CARE <span aria-hidden="true">·</span> 2026</p>
  </main>
</template>

<style scoped>
.page-shell {
  position: relative;
  isolation: isolate;
  display: flex;
  min-height: 100vh;
  min-height: 100svh;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  padding: 48px 20px 30px;
  background:
    radial-gradient(ellipse at 50% 10%, rgba(159, 204, 105, 0.09), transparent 46%),
    var(--page);
  transition: background-color 280ms ease;
}

.ambient {
  position: absolute;
  z-index: -1;
  width: 360px;
  height: 360px;
  border: 1px solid rgba(197, 242, 123, 0.08);
  border-radius: 50%;
  pointer-events: none;
}

.ambient-one {
  top: -210px;
  right: -95px;
}

.ambient-two {
  bottom: -270px;
  left: -115px;
  width: 460px;
  height: 460px;
}

.profile-card {
  width: min(100%, 480px);
  padding: 27px clamp(22px, 6vw, 38px) 24px;
  border: 1px solid var(--card-border);
  border-radius: 28px;
  background: var(--card);
  box-shadow:
    0 30px 90px var(--shadow),
    inset 0 1px 0 rgba(255, 255, 255, 0.035);
  backdrop-filter: blur(18px);
  transition:
    background-color 280ms ease,
    border-color 280ms ease,
    box-shadow 280ms ease;
}

.card-topline {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  color: var(--muted);
  font-size: 10px;
  font-weight: 700;
  letter-spacing: 0.16em;
}

.status-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--accent);
  box-shadow: 0 0 12px color-mix(in srgb, var(--accent) 60%, transparent);
}

.theme-toggle {
  display: inline-flex;
  min-height: 36px;
  align-items: center;
  gap: 7px;
  padding: 0 11px;
  border: 1px solid var(--card-border);
  border-radius: 999px;
  color: var(--muted);
  background: transparent;
  cursor: pointer;
  font-size: 11px;
  font-weight: 600;
  transition:
    color 180ms ease,
    border-color 180ms ease,
    background-color 180ms ease;
}

.theme-toggle:hover {
  border-color: color-mix(in srgb, var(--accent) 40%, var(--card-border));
  color: var(--text);
  background: var(--surface);
}

.theme-toggle:focus-visible,
.link-card:focus-visible {
  outline: 2px solid var(--accent);
  outline-offset: 4px;
}

.theme-toggle svg {
  width: 15px;
  height: 15px;
}

.profile-header {
  padding: 29px 0 27px;
  text-align: center;
}

.avatar {
  position: relative;
  display: grid;
  width: 94px;
  height: 94px;
  margin: 0 auto 20px;
  place-items: center;
  border: 1px solid rgba(197, 242, 123, 0.35);
  border-radius: 50%;
  color: var(--accent);
  background:
    radial-gradient(circle at 35% 25%, rgba(197, 242, 123, 0.18), transparent 48%),
    linear-gradient(145deg, var(--surface-hover), var(--surface));
  box-shadow:
    0 0 0 6px color-mix(in srgb, var(--accent) 7%, transparent),
    inset 0 1px 10px rgba(255, 255, 255, 0.04);
  font-size: 25px;
  font-weight: 600;
  letter-spacing: -0.06em;
}

.avatar-sparkle {
  position: absolute;
  right: -1px;
  bottom: 4px;
  display: grid;
  width: 25px;
  height: 25px;
  place-items: center;
  border: 3px solid var(--card);
  border-radius: 50%;
  color: var(--accent-ink);
  background: var(--accent);
  font-size: 11px;
  letter-spacing: normal;
}

h1 {
  color: var(--text);
  font-size: clamp(27px, 7vw, 32px);
  font-weight: 600;
  letter-spacing: -0.055em;
  line-height: 1.15;
}

.tagline {
  max-width: 310px;
  margin: 10px auto 0;
  color: var(--muted);
  font-size: 13px;
  line-height: 1.65;
}

.link-list {
  display: grid;
  gap: 10px;
}

.link-card {
  display: flex;
  min-height: 67px;
  align-items: center;
  gap: 14px;
  padding: 11px 14px;
  border: 1px solid transparent;
  border-radius: 15px;
  background: var(--surface);
  transition:
    transform 200ms ease,
    border-color 200ms ease,
    background-color 200ms ease,
    box-shadow 200ms ease;
}

.link-card:hover {
  transform: translateY(-3px);
  border-color: color-mix(in srgb, var(--accent) 34%, transparent);
  background: var(--surface-hover);
  box-shadow: 0 9px 22px var(--shadow);
}

.link-icon {
  display: grid;
  width: 40px;
  height: 40px;
  flex: 0 0 40px;
  place-items: center;
  border: 1px solid var(--card-border);
  border-radius: 12px;
  color: var(--accent);
  background: color-mix(in srgb, var(--accent) 8%, var(--surface));
}

.link-icon svg {
  width: 21px;
  height: 21px;
}

.link-copy {
  display: grid;
  min-width: 0;
  gap: 2px;
}

.link-title {
  color: var(--text);
  font-size: 13px;
  font-weight: 600;
  letter-spacing: -0.01em;
}

.link-detail {
  overflow: hidden;
  color: var(--muted);
  font-size: 11px;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.link-arrow {
  width: 17px;
  height: 17px;
  flex: 0 0 17px;
  margin-left: auto;
  color: var(--subtle);
  transition:
    color 200ms ease,
    transform 200ms ease;
}

.link-card:hover .link-arrow {
  transform: translateX(3px);
  color: var(--accent);
}

.card-footer {
  display: flex;
  align-items: center;
  gap: 11px;
  margin-top: 23px;
  color: var(--subtle);
  font-size: 10px;
  font-weight: 500;
  white-space: nowrap;
}

.footer-rule {
  height: 1px;
  flex: 1;
  background: var(--card-border);
}

.footer-star {
  padding-left: 2px;
  color: var(--accent);
}

.page-credit {
  margin-top: 22px;
  color: var(--subtle);
  font-size: 9px;
  font-weight: 600;
  letter-spacing: 0.2em;
}

.page-credit span {
  padding: 0 3px;
  color: var(--accent);
}

@media (max-width: 380px) {
  .page-shell {
    padding-right: 14px;
    padding-left: 14px;
  }

  .profile-card {
    padding-right: 20px;
    padding-left: 20px;
  }

  .link-card {
    gap: 11px;
    padding-right: 11px;
    padding-left: 11px;
  }
}

@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    scroll-behavior: auto !important;
    transition-duration: 0.01ms !important;
  }
}
</style>

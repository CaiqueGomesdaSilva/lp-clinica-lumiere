<script setup lang="ts">
interface NavLink {
  label: string
  href: string
}

interface Props {
  logo: string
  links: NavLink[]
  cta: string
}

defineProps<Props>()
</script>

<template>
  <nav class="navbar">
    <div class="container navbar-inner">
      <span class="navbar-logo">{{ logo }}</span>
      <div class="navbar-links">
        <a
          v-for="link in links"
          :key="link.href"
          :href="link.href"
          class="navbar-link"
        >{{ link.label }}</a>
      </div>
      <a href="#avaliacao" class="btn-nav">{{ cta }}</a>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: sticky;
  top: 0;
  z-index: 100;
  background: var(--color-bg);
  border-bottom: 1px solid var(--color-border);
}

.navbar-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 68px;
}

.navbar-logo {
  font-family: var(--font-title);
  font-size: 22px;
  color: var(--color-text);
  letter-spacing: 0.04em;
}

.navbar-links {
  display: flex;
  gap: 32px;
}

.navbar-link {
  font-family: var(--font-body);
  font-size: 14px;
  color: var(--color-text-muted);
  transition: color 200ms;
}

.navbar-link:hover {
  color: var(--color-text);
}

.btn-nav {
  font-family: var(--font-body);
  font-size: 14px;
  font-weight: 500;
  color: #fff;
  background: var(--color-rose);
  padding: 10px 24px;
  border-radius: 30px;
  transition: opacity 200ms;
}

.btn-nav:hover {
  opacity: 0.88;
}

@media (max-width: 768px) {
  .navbar-links {
    display: none;
  }
}
</style>

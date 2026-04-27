<script setup lang="ts">
interface Props {
  badge: string
  titulo: string
  subtitulo: string
  btnPrimario: string
  btnSecundario: string
  foto: string
  fotoAlt: string
}

defineProps<Props>()
</script>

<template>
  <section class="hero">
    <div class="container hero-inner">
      <div class="hero-text">
        <span class="hero-badge">{{ badge }}</span>
        <div class="hero-linha" />
        <h1 class="hero-titulo">{{ titulo }}</h1>
        <p class="hero-subtitulo">{{ subtitulo }}</p>
        <div class="hero-btns">
          <a href="#avaliacao" class="btn-primary">{{ btnPrimario }}</a>
          <a href="#procedimentos" class="btn-secondary">{{ btnSecundario }}</a>
        </div>
      </div>
      <div class="hero-image">
        <img :src="foto" :alt="fotoAlt" class="hero-foto" />
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  background: var(--color-bg);
}

.hero-inner {
  display: flex;
  align-items: center;
  min-height: 100vh;
  gap: 60px;
  padding-top: 40px;
  padding-bottom: 40px;
}

.hero-text {
  flex: 0 0 55%;
}

.hero-badge {
  display: inline-block;
  font-family: var(--font-body);
  font-size: 11px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--color-rose);
  background: var(--color-rose-light);
  border-radius: 20px;
  padding: 4px 14px;
  margin-bottom: 18px;
}

.hero-linha {
  width: 40px;
  height: 1px;
  background: var(--color-rose);
  margin-bottom: 22px;
}

.hero-titulo {
  font-family: var(--font-title);
  font-size: 68px;
  font-weight: 300;
  line-height: 1.1;
  color: var(--color-text);
  white-space: pre-line;
  margin-bottom: 24px;
}

.hero-subtitulo {
  font-family: var(--font-body);
  font-size: 17px;
  font-weight: 300;
  color: var(--color-text-muted);
  line-height: 1.7;
  margin-bottom: 40px;
  max-width: 440px;
}

.hero-btns {
  display: flex;
  align-items: center;
  gap: 28px;
  flex-wrap: wrap;
}

.btn-primary {
  font-family: var(--font-body);
  font-size: 15px;
  font-weight: 500;
  color: #fff;
  background: var(--color-rose);
  padding: 14px 32px;
  border-radius: 30px;
  transition: opacity 200ms;
  white-space: nowrap;
}

.btn-primary:hover {
  opacity: 0.88;
}

.btn-secondary {
  font-family: var(--font-body);
  font-size: 15px;
  font-weight: 400;
  color: var(--color-text);
  transition: color 200ms;
  white-space: nowrap;
}

.btn-secondary:hover {
  color: var(--color-rose);
}

.hero-image {
  flex: 1;
  height: 68vh;
  min-height: 420px;
}

.hero-foto {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 16px;
}

@media (max-width: 768px) {
  .hero-inner {
    flex-direction: column-reverse;
    min-height: auto;
    gap: 32px;
    padding-top: 48px;
    padding-bottom: 64px;
  }

  .hero-text {
    flex: none;
    width: 100%;
  }

  .hero-titulo {
    font-size: 40px;
  }

  .hero-image {
    width: 100%;
    height: 280px;
    min-height: unset;
  }

  .hero-btns {
    flex-direction: column;
    align-items: stretch;
    gap: 16px;
  }

  .btn-primary,
  .btn-secondary {
    text-align: center;
    width: 100%;
  }
}
</style>

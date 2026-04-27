<script setup lang="ts">
interface Depoimento {
  nome: string
  tempo: string
  texto: string
  iniciais: string
}

interface Props {
  titulo: string
  itens: Depoimento[]
}

defineProps<Props>()
</script>

<template>
  <section class="depoimentos">
    <div class="container">
      <div class="secao-header">
        <h2 class="secao-titulo">{{ titulo }}</h2>
      </div>
      <div class="depoimentos-grid">
        <div
          v-for="dep in itens"
          :key="dep.nome"
          class="card-depoimento"
        >
          <span class="card-aspas">"</span>
          <p class="card-texto">{{ dep.texto }}</p>
          <div class="card-autor">
            <div class="card-avatar">{{ dep.iniciais }}</div>
            <div class="card-info">
              <span class="card-nome">{{ dep.nome }}</span>
              <span class="card-tempo">{{ dep.tempo }}</span>
            </div>
            <div class="card-estrelas">★★★★★</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.depoimentos {
  background: var(--color-bg-section);
  padding: 110px 0;
}

.secao-header {
  text-align: center;
  margin-bottom: 56px;
}

.secao-titulo {
  font-family: var(--font-title);
  font-size: 42px;
  font-weight: 400;
  color: var(--color-text);
}

.depoimentos-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

.card-depoimento {
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: 12px;
  padding: 36px 28px 28px;
  display: flex;
  flex-direction: column;
  gap: 16px;
  box-shadow: 0 2px 16px rgba(0, 0, 0, 0.06);
  position: relative;
}

.card-aspas {
  font-family: var(--font-title);
  font-size: 64px;
  line-height: 1;
  color: var(--color-rose);
  opacity: 0.3;
  position: absolute;
  top: 16px;
  left: 24px;
}

.card-texto {
  font-family: var(--font-body);
  font-size: 15px;
  color: var(--color-text);
  line-height: 1.7;
  padding-top: 20px;
  flex: 1;
}

.card-autor {
  display: flex;
  align-items: center;
  gap: 12px;
  padding-top: 16px;
  border-top: 1px solid var(--color-border);
}

.card-avatar {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: var(--color-rose-light);
  color: var(--color-rose);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--font-body);
  font-size: 13px;
  font-weight: 500;
  flex-shrink: 0;
}

.card-info {
  display: flex;
  flex-direction: column;
  gap: 2px;
  flex: 1;
}

.card-nome {
  font-family: var(--font-body);
  font-size: 14px;
  font-weight: 500;
  color: var(--color-text);
}

.card-tempo {
  font-family: var(--font-body);
  font-size: 12px;
  color: var(--color-text-muted);
}

.card-estrelas {
  font-size: 14px;
  color: var(--color-rose);
  letter-spacing: 1px;
}

@media (max-width: 768px) {
  .depoimentos-grid {
    grid-template-columns: 1fr;
  }
}
</style>

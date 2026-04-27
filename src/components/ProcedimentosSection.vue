<script setup lang="ts">
interface Procedimento {
  nome: string
  descricao: string
  duracao: string
  preco: string
}

interface Props {
  titulo: string
  subtitulo: string
  itens: Procedimento[]
}

defineProps<Props>()

const icones: string[] = [
  `<svg viewBox="0 0 24 24" width="20" height="20"><path fill="currentColor" d="M12 2.69l5.66 5.66a8 8 0 1 1-11.31 0z"/></svg>`,
  `<svg viewBox="0 0 24 24" width="20" height="20"><polygon fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/></svg>`,
  `<svg viewBox="0 0 24 24" width="20" height="20"><polyline fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" points="1 4 1 10 7 10"/><path fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" d="M3.51 15a9 9 0 1 0 .49-3.1"/></svg>`,
  `<svg viewBox="0 0 24 24" width="20" height="20"><polygon fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/></svg>`,
  `<svg viewBox="0 0 24 24" width="20" height="20"><polygon fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" points="12 2 2 7 12 12 22 7 12 2"/><polyline fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" points="2 17 12 22 22 17"/><polyline fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" points="2 12 12 17 22 12"/></svg>`,
  `<svg viewBox="0 0 24 24" width="20" height="20"><polyline fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>`,
]
</script>

<template>
  <section class="procedimentos">
    <div class="container">
      <div class="secao-header">
        <h2 class="secao-titulo">{{ titulo }}</h2>
        <p class="secao-subtitulo">{{ subtitulo }}</p>
      </div>
      <div class="procedimentos-grid">
        <div
          v-for="(proc, i) in itens"
          :key="proc.nome"
          class="card-procedimento"
        >
          <div class="card-icone">
            <span v-html="icones[i]" />
          </div>
          <span class="card-label">{{ proc.nome }}</span>
          <p class="card-descricao">{{ proc.descricao }}</p>
          <div class="card-rodape">
            <span class="card-duracao">{{ proc.duracao }}</span>
            <span class="card-preco">{{ proc.preco }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.procedimentos {
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
  margin-bottom: 12px;
}

.secao-subtitulo {
  font-family: var(--font-body);
  font-size: 17px;
  font-weight: 300;
  color: var(--color-text-muted);
}

.procedimentos-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

.card-procedimento {
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: 12px;
  padding: 32px 28px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  transition: border-color 200ms;
  box-shadow: 0 2px 16px rgba(0, 0, 0, 0.06);
}

.card-procedimento:hover {
  border-color: var(--color-rose);
}

.card-icone {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background: var(--color-rose-light);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--color-rose);
  margin-bottom: 4px;
}

.card-label {
  font-family: var(--font-body);
  font-size: 12px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--color-text);
}

.card-descricao {
  font-family: var(--font-body);
  font-size: 14px;
  color: var(--color-text-muted);
  line-height: 1.6;
  flex: 1;
}

.card-rodape {
  display: flex;
  flex-direction: column;
  gap: 2px;
  margin-top: 8px;
  padding-top: 16px;
  border-top: 1px solid var(--color-border);
}

.card-duracao {
  font-family: var(--font-body);
  font-size: 13px;
  color: var(--color-text-muted);
}

.card-preco {
  font-family: var(--font-body);
  font-size: 13px;
  font-weight: 500;
  color: var(--color-rose);
}

@media (max-width: 768px) {
  .procedimentos-grid {
    grid-template-columns: 1fr;
  }
}
</style>

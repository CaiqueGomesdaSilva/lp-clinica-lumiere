<script setup lang="ts">
interface Diferencial {
  numero: string
  titulo: string
  descricao: string
}

interface Props {
  titulo: string
  itens: Diferencial[]
}

defineProps<Props>()
</script>

<template>
  <section class="diferenciais">
    <div class="container diferenciais-inner">
      <div class="diferenciais-heading">
        <h2 class="secao-titulo">{{ titulo }}</h2>
      </div>
      <div class="diferenciais-grid">
        <div
          v-for="item in itens"
          :key="item.numero"
          class="diferencial-item"
        >
          <span class="diferencial-numero">{{ item.numero }}</span>
          <h3 class="diferencial-titulo">{{ item.titulo }}</h3>
          <p class="diferencial-descricao">{{ item.descricao }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.diferenciais {
  background: var(--color-bg);
  padding: 110px 0;
}

.diferenciais-inner {
  display: flex;
  gap: 80px;
  align-items: flex-start;
}

.diferenciais-heading {
  flex: 0 0 38%;
}

.secao-titulo {
  font-family: var(--font-title);
  font-size: 42px;
  font-weight: 400;
  color: var(--color-text);
  line-height: 1.2;
  position: sticky;
  top: 100px;
}

.diferenciais-grid {
  flex: 1;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 40px 32px;
}

.diferencial-item {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.diferencial-numero {
  font-family: var(--font-title);
  font-size: 52px;
  font-weight: 300;
  color: var(--color-rose);
  line-height: 1;
  margin-bottom: 4px;
}

.diferencial-titulo {
  font-family: var(--font-body);
  font-size: 15px;
  font-weight: 500;
  color: var(--color-text);
}

.diferencial-descricao {
  font-family: var(--font-body);
  font-size: 14px;
  color: var(--color-text-muted);
  line-height: 1.65;
}

@media (max-width: 768px) {
  .diferenciais-inner {
    flex-direction: column;
    gap: 40px;
  }

  .diferenciais-heading {
    flex: none;
  }

  .secao-titulo {
    position: static;
    font-size: 36px;
  }

  .diferenciais-grid {
    grid-template-columns: 1fr;
    gap: 32px;
  }

  .diferencial-numero {
    font-size: 40px;
  }
}
</style>

<script setup lang="ts">
interface Props {
  texto: string
}

defineProps<Props>()
</script>

<template>
  <footer class="footer">
    <div class="container footer-inner">
      <p class="footer-texto">{{ texto }}</p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: var(--color-bg-section);
  border-top: 1px solid var(--color-border);
  padding: 32px 0;
}

.footer-inner {
  display: flex;
  justify-content: center;
}

.footer-texto {
  font-family: var(--font-body);
  font-size: 13px;
  color: var(--color-text-muted);
  text-align: center;
}
</style>

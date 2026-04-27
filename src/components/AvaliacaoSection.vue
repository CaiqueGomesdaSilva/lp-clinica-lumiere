<script setup lang="ts">
import { ref, computed } from 'vue'

interface Props {
  titulo: string
  subtitulo: string
  btnTexto: string
  nota: string
  procedimentosSelect: string[]
  whatsappUrl: string
}

const props = defineProps<Props>()

const form = ref({
  nome: '',
  telefone: '',
  procedimento: '',
})

const phone = computed(() => {
  const match = props.whatsappUrl.match(/wa\.me\/(\d+)/)
  return match ? match[1] : '5511999990000'
})

function enviar() {
  const { nome, telefone, procedimento } = form.value
  const msg = `Olá! Quero agendar uma avaliação.\nNome: ${nome}\nTelefone: ${telefone}\nInteresse: ${procedimento || 'não informado'}`
  window.open(`https://wa.me/${phone.value}?text=${encodeURIComponent(msg)}`, '_blank')
}
</script>

<template>
  <section class="avaliacao">
    <div class="container avaliacao-inner">
      <h2 class="avaliacao-titulo">{{ titulo }}</h2>
      <p class="avaliacao-subtitulo">{{ subtitulo }}</p>
      <form class="avaliacao-form" @submit.prevent="enviar">
        <div class="campo">
          <label class="campo-label" for="av-nome">Nome</label>
          <input
            id="av-nome"
            v-model="form.nome"
            type="text"
            class="campo-input"
            placeholder="Seu nome completo"
            required
          />
        </div>
        <div class="campo">
          <label class="campo-label" for="av-telefone">Telefone</label>
          <input
            id="av-telefone"
            v-model="form.telefone"
            type="tel"
            class="campo-input"
            placeholder="(11) 99999-0000"
            required
          />
        </div>
        <div class="campo">
          <label class="campo-label" for="av-procedimento">Procedimento de interesse</label>
          <select
            id="av-procedimento"
            v-model="form.procedimento"
            class="campo-input"
          >
            <option value="">Selecione um procedimento</option>
            <option
              v-for="p in procedimentosSelect"
              :key="p"
              :value="p"
            >{{ p }}</option>
          </select>
        </div>
        <button type="submit" class="btn-avaliacao">{{ btnTexto }}</button>
        <p class="avaliacao-nota">{{ nota }}</p>
      </form>
    </div>
  </section>
</template>

<style scoped>
.avaliacao {
  background: var(--color-bg);
  padding: 110px 0;
}

.avaliacao-inner {
  max-width: 560px;
  text-align: center;
}

.avaliacao-titulo {
  font-family: var(--font-title);
  font-size: 42px;
  font-weight: 400;
  color: var(--color-text);
  margin-bottom: 12px;
}

.avaliacao-subtitulo {
  font-family: var(--font-body);
  font-size: 17px;
  font-weight: 300;
  color: var(--color-text-muted);
  line-height: 1.65;
  margin-bottom: 40px;
}

.avaliacao-form {
  display: flex;
  flex-direction: column;
  text-align: left;
}

.campo {
  display: flex;
  flex-direction: column;
  gap: 6px;
  margin-bottom: 16px;
}

.campo-label {
  font-family: var(--font-body);
  font-size: 12px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--color-text-muted);
}

.campo-input {
  font-family: var(--font-body);
  font-size: 15px;
  color: var(--color-text);
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: 8px;
  padding: 13px 16px;
  width: 100%;
  outline: none;
  transition: border-color 200ms;
  appearance: none;
  -webkit-appearance: none;
}

.campo-input:focus {
  border-color: var(--color-rose);
}

.campo-input::placeholder {
  color: var(--color-border);
}

.btn-avaliacao {
  width: 100%;
  padding: 16px;
  border-radius: 30px;
  background: var(--color-rose);
  color: #fff;
  font-family: var(--font-body);
  font-size: 16px;
  font-weight: 500;
  border: none;
  cursor: pointer;
  transition: opacity 200ms;
  margin-top: 8px;
}

.btn-avaliacao:hover {
  opacity: 0.88;
}

.avaliacao-nota {
  font-family: var(--font-body);
  font-size: 13px;
  color: var(--color-text-muted);
  text-align: center;
  margin-top: 14px;
}
</style>

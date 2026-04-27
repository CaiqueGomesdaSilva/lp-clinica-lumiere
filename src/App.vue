<script setup lang="ts">
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import ProcedimentosSection from './components/ProcedimentosSection.vue'
import DiferenciaisSection from './components/DiferenciaisSection.vue'
import DepoimentosSection from './components/DepoimentosSection.vue'
import AvaliacaoSection from './components/AvaliacaoSection.vue'
import FooterSection from './components/FooterSection.vue'
import WhatsappButton from './components/WhatsappButton.vue'

import {
  nav,
  hero,
  secoes,
  procedimentos,
  diferenciais,
  depoimentos,
  procedimentosSelect,
  avaliacao,
  footer,
  whatsappUrl,
} from './data'
</script>

<template>
  <NavBar v-bind="nav" />
  <main>
    <HeroSection v-bind="hero" />
    <ProcedimentosSection
      id="procedimentos"
      :titulo="secoes.procedimentos.titulo"
      :subtitulo="secoes.procedimentos.subtitulo"
      :itens="procedimentos"
    />
    <DiferenciaisSection
      id="diferenciais"
      :titulo="secoes.diferenciais.titulo"
      :itens="diferenciais"
    />
    <DepoimentosSection
      id="depoimentos"
      :titulo="secoes.depoimentos.titulo"
      :itens="depoimentos"
    />
    <AvaliacaoSection
      id="avaliacao"
      v-bind="avaliacao"
      :procedimentos-select="procedimentosSelect"
      :whatsapp-url="whatsappUrl"
    />
  </main>
  <FooterSection v-bind="footer" />
  <WhatsappButton :url="whatsappUrl" />
</template>

<style scoped></style>

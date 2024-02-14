<template>
  <main>
    <article>
      <div class="flex justify-around">
      <h3 class="text-slate-300">Mis albums</h3>
      <ButtonSecondary>Editar</ButtonSecondary>
      </div>
      <section class="grid grid-cols-2">
        <ButtonDefault>English</ButtonDefault>
        <ButtonDefault>Algebra</ButtonDefault>
        <ButtonDefault>Frances</ButtonDefault>
        <ButtonDefault>Programación</ButtonDefault>
      </section>
    </article>
  </main>
</template>

<script setup>
import ButtonDefault from '../components/ButtonDefault.vue'
import ButtonSecondary from '../components/ButtonSecondary.vue'
</script>
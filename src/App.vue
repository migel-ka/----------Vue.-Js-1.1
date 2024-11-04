<script setup>
import ToDo from "./components/ToDo.vue";
</script>

<template>
  <section class="container">
    <h1>НезабывайКа</h1>
    <ToDo />
  </section>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 5% 10%;

h1 {
  font-size: 30px;
}
}
</style>

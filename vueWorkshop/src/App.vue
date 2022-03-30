<script setup>
import Header from './components/header.vue'
import Todo from './components/todo.vue'
</script>

<template>
  <div>
    <Header />
    <div id="container">
    <Todo/>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  #container {
    max-width: min(90%, 80rem);
    margin: 2rem auto;
  }
</style>

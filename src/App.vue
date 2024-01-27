<template>
  <h1>Vue3練習場</h1>
  <CurrencyExchange />
  <ModifiersClass/>
  <ToDoList />
</template>

<script>
import CurrencyExchange from './components/CurrencyExchange.vue';
import ModifiersClass from './components/ModifiersClass.vue';
import ToDoList from './components/ToDoList.vue';

export default {
  components: {
    CurrencyExchange,
    ModifiersClass,
    ToDoList
  },
};
</script>

<style>
body {
  padding: 1rem;
}
</style>

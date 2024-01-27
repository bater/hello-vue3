<template>
  <div id="app">
    <h1>Vue3練習場</h1>
    <CurrencyExchange />
    <ModifiersClass/>
  </div>
</template>

<script>
import CurrencyExchange from './components/CurrencyExchange.vue';
import ModifiersClass from './components/ModifiersClass.vue';

export default {
  components: {
    CurrencyExchange,
    ModifiersClass
  },
};
</script>

<style>
body {
  padding: 1rem;
}
</style>

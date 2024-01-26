<template>
  <div id="app">
    <CurrencyExchange />
  </div>
</template>

<script>
import CurrencyExchange from './components/CurrencyExchange.vue';

export default {
  components: {
    CurrencyExchange,
  },
};
</script>

<style>
body {
  padding: 1rem;
}
</style>

<template>
  <div id="app">
    <h1>Vue3練習場</h1>
    <RecursiveComponent />
    <CurrencyExchange />
    <ModifiersClass/>
    <ToDoList />
    <TreeNode />
  </div>
</template>

<script>
import CurrencyExchange from './components/CurrencyExchange.vue';
import ModifiersClass from './components/ModifiersClass.vue';
import ToDoList from './components/ToDoList.vue';
import TreeNode from './components/TreeNode.vue';
import RecursiveComponent from './components/RecursiveComponent.vue';

export default {
  components: {
    CurrencyExchange,
    ModifiersClass,
    ToDoList,
    TreeNode,
    RecursiveComponent,
  },
};
</script>

<style>
body {
  padding: 1rem;
}
</style>

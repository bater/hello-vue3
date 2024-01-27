<template>
  <h2>動態元件範例</h2>
  <div id="app6">
  <button
    v-for="tab in tabs"
    :key="tab"
    :class="['tab-button', { active: currentTab === tab }]"
    @click="currentTab = tab">
    {{ tab }}
  </button>
  <component :is="currentTabComponent"></component>
</div>
</template>
<script>
import { defineComponent } from 'vue';

const TabHome = defineComponent({
  template: `<div class="demo-tab">Home component</div>`
})

const TabPosts = defineComponent({
  template: `<div class="demo-tab">Posts component</div>`
})

const TabArchive = defineComponent({
  template: `<div class="demo-tab">Archive component</div>`
})

export default defineComponent({
  components: {
    TabHome,
    TabPosts,
    TabArchive
  },
  data() {
    return {
      currentTab: 'Home',
      tabs: ['Home', 'Posts', 'Archive']
    }
  },
  computed: {
    currentTabComponent() {
      return `Tab${ this.currentTab }`;
    }
  }
});

</script>
<style scoped>
#app6 {
  font-family: sans-serif;
  border: 1px solid #eee;
  border-radius: 2px;
  padding: 20px 30px;
  margin-top: 1em;
  margin-bottom: 40px;
  user-select: none;
  overflow-x: auto;
}

.tab-button {
  padding: 6px 10px;
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
  border: 1px solid #ccc;
  cursor: pointer;
  background: #f0f0f0;
  margin-bottom: -1px;
  margin-right: -1px;
}
.tab-button:hover {
  background: #e0e0e0;
}
.tab-button.active {
  background: #e0e0e0;
}
.demo-tab {
  border: 1px solid #ccc;
  padding: 10px;
}

.dynamic-component-demo-posts-tab {
  li {
    margin-bottom: 1.5rem;
  }
}
</style>
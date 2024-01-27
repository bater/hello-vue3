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
  <keep-alive include="tab-home,tab-posts" :max="2">
    <component :is="currentTabComponent"></component>
  </keep-alive>
</div>
</template>
<script>
import { defineComponent } from 'vue';

const TabHome = defineComponent({
  name: 'tab-home',
  template: `<div class="demo-tab"><input v-model="title"></div>`,
  data: () => ({ title: 'Home component' })
})

const TabPosts = defineComponent({
  name: 'tab-posts',
  template: `<div class="demo-tab"><input v-model="title"></div>`,
  data: () => ({ title: 'Posts component' })
})

const TabArchive = defineComponent({
  name: 'tab-archive',
  template: `<div class="demo-tab"><input v-model="title"></div>`,
  data: () => ({ title: 'Archive component' })
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

input {
  min-width: 350px;
  padding: 3px 5px;
  font-size: 1rem;
}
</style>
<template>
  <div class="app5">
    <h2>推薦書籍範例</h2>
    <MenuComponent :title="menuData.name" :child="menuData.childNodes"></MenuComponent>
  </div>
  <hr>
</template>

<script>
import { defineComponent } from 'vue';

const menuData = {
  name: '好書推薦',
  childNodes: [{
      name: 'Git',
      url: null,
      childNodes: [{
        name: '為你自己學 Git',
        url: 'https://www.tenlong.com.tw/products/9789864342662'
      }]
    },
    {
      name: '前端開發',
      url: null,
      childNodes: [{
          name: '金魚都能懂的 CSS 選取器',
          url: 'https://www.tenlong.com.tw/products/9789864344994'
        },
        {
          name: '0 陷阱！0 誤解！8 天重新認識 JavaScript！',
          url: 'https://www.tenlong.com.tw/products/9789864344130'
        },
        {
          name: '讓 TypeScript 成為你全端開發的 ACE！',
          url: 'https://www.tenlong.com.tw/products/9789864344895'
        },
      ]
    },
    {
      name: 'IoT',
      url: null,
      childNodes: [{
        name: 'IoT沒那麼難！新手用 JavaScript 入門做自己的玩具！',
        url: 'https://www.tenlong.com.tw/products/9789864345328'
      }]
    },
    {
      name: 'Chatbot',
      url: null,
      childNodes: [{
        name: '人人可作卡米狗：從零打造自己的 LINE 聊天機器人',
        url: 'https://www.tenlong.com.tw/products/9789864342938'
      }]
    }
  ]
};

const MenuComponent = defineComponent({
  name: 'MenuComponent',
  props: {
    title: String,
    url: String,
    child: {
      type: Array,
      default: () => []
    }
  },
  setup(props) {
    return props;
  },
  data() {
    return {
      isOpen: false
    }
  },
  template: `
    <ul>
      <li>
        <template v-if="child.length > 0">
          <h2 class="has-child"
            :class="{ 'is-open': isOpen }"
            @click="isOpen = !isOpen">{{ title }}</h2>
          <menu-component
            v-show="isOpen"
            v-for="c in child"
            :title="c.name"
            :child="c.childNodes"
            :url="c.url"
            />
        </template>
        <a :href="url" target="_blank" v-else>{{ title }}</a>
      </li>
    </ul>`
});

export default defineComponent({
  components: {
    MenuComponent,
  },
  data() {
    return {
      menuData
    };
  },
});
</script>

<style scoped>
#app5 {
  display: block;
  padding: 1rem;
  font-size: 1rem;
}

#app5 > ul {
  > li {
    margin-left: 0;
  }
}

ul > li {
  display: block;
  margin-left: 1rem;
  margin-bottom: 0.5rem;
  padding: 8px;
  background-color: #eee;
}

h2.has-child {
  cursor: pointer;

  &::before {
    content: '+ ';
  }
}

h2.has-child.is-open::before {
  content: '- ';
}

a {
  color: #333;
  text-decoration: none;
  &:hover { color: red; }
}

</style>
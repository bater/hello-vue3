<template>
  <div>
    <h2>Recursive Tree Component</h2>
    <TreeNode :node="treeData" />
  </div>
  <hr>
</template>

<script>
import { defineComponent } from 'vue';

const TreeNode = defineComponent({
  name: 'TreeNode',
  props: {
    node: {
      name: String,
      children: {
        type: Array,
        default: []
      }
    },
  },
  setup(props) {
    return props;
  },
  template: `
    <div>
      {{ node.name }}
      <ul v-if="node.children && node.children.length">
        <TreeNode v-for="child in node.children" :key="child.name" :node="child" />
      </ul>
    </div>
  `,
});

export default defineComponent({
  components: {
    TreeNode,
  },
  data() {
    return {
      treeData: {
        name: 'Root',
        children: [
          {
            name: 'Node 1',
            children: [
              {
                name: 'Node 1.1',
                children: [
                  { name: 'Node 1.1.1' },
                  { name: 'Node 1.1.2' },
                ] },
              { name: 'Node 1.2' },
            ],
          },
          {
            name: 'Node 2',
            children: [
              { name: 'Node 2.1' },
              { name: 'Node 2.2' },
            ],
          },
        ],
      },
    };
  },
});
</script>

<style scoped>
.arrow-open {
  transform: rotate(90deg);
  display: inline-block;
}

.arrow-closed {
  transform: rotate(0deg);
  display: inline-block;
}

ul {
  list-style-type: none;
  padding-left: 20px;
}
</style>

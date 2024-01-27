<template>
  <div class="example3">
    <h2>Todo List</h2>
    <div class="wrap">
      <div class="todo-lists">
        <h3>Todo</h3>
        <ul>
          <li v-for="i in todoLists" :key="i.id">
            <label><input v-model="i.isDone" type="checkbox"> {{ i.title }}</label>
          </li>
        </ul>
      </div>

      <div class="done-lists">
        <h3>Done</h3>
        <ul>
          <li v-for="i in doneLists" :key="i.id">
            <label><input v-model="i.isDone" type="checkbox"> {{ i.title }}</label>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      lists: [{
          id: 'task001',
          title: '選項 1',
          isDone: false
        },
        {
          id: 'task002',
          title: '選項 2',
          isDone: false
        },
        {
          id: 'task003',
          title: '選項 3',
          isDone: false
        },
      ]
    }
  },
  computed: {
    todoLists() {
      return this.lists.filter(d => !d.isDone)
    },
    doneLists() {
      return this.lists.filter(d => d.isDone)
    },
  }
};
</script>
<style scoped>
.example3 {
  display: block;
  padding: 1rem;
  font-size: 1rem;
}

h3 {
  margin-bottom: 1rem;
}

.wrap {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  overflow: hidden;
}

.todo-lists, .done-lists {
  display: block;
  max-width: 150px;
  width: 45%;
  margin-right: 4%;
  float: left;
  border: 1px solid #ccc;
  padding: 1rem;
  align-self: flex-start;
}

li {
  margin-bottom: 5px;
}
</style>
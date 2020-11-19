<template>
  <div>
    <TodoList
    v-bind:todos="todos"
    @remove-todo="removeTodo"
  />
  <AddTodo
    @add-todo="addTodo"
  />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList';
import AddTodo from '@/components/AddTodo';

export default {
  components: {
    TodoList,
    AddTodo,
  },
  data() {
    return {
      todos: [
        { id: 1, title: 'firstTitle', completed: false },
        { id: 2, title: 'secondTitle', completed: false },
        { id: 3, title: 'thirdTitle', completed: false },
      ],
    };
  },

  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos')
      .then((response) => response.json())
      .then((json) => {
        this.todos = json.slice(0, 10);
      });
  },

  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    },
  },
};
</script>

<style scoped>

</style>

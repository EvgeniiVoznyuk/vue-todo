<template>
  <ul class="list">
    <TodoItem
      v-bind:key="todo.id"
      v-for="(todo, i) of todos"
      v-bind:index="i"
      v-bind:todo="todo"
      v-on:remove-todo="removeTodo"
    />
  </ul>
</template>

<script>
import TodoItem from '@/components/TodoItem';

export default {
  props: ['todos'],
  components: {
    TodoItem,
  },
  methods: {
    removeTodo(id) {
      this.$emit('remove-todo', id);
    },
  },
};
</script>

<style lang="scss" scoped>
  .list {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>

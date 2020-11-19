<template>
  <li class="list__item item">
    <span v-bind:class="{done: todo.completed, item__span: true}">
      <input
        type="checkbox"
        class="item__input"
        v-on:change="todo.completed = !todo.completed"
      >
      <strong class="item__id">{{index + 1}}.</strong>
      {{todo.title}}
    </span>
    <button
      class="item__button"
      v-on:click="$emit('remove-todo', todo.id)"
    >
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    index: Number,
  },
};
</script>

<style lang="scss" scoped>
  .item {
    list-style: none;
    display: flex;
    justify-content: space-between;
    width: 400px;
    border:1px solid black;
    padding: 10px;
    margin: 10px;
    border-radius: 10px;

    &__span {
      display: flex;
      gap: 5px;
    }

    &__button {
      width: 20px;
      height: 20px;
      background-color: red;
      color: #fff;
      font-weight: bold;
      border:none;
      border-radius: 5px;
      cursor: pointer;
    }
  }

  .done {
    text-decoration: line-through;
  }
</style>

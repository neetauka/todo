<template>
  <div>
    <section v-if="todos.length > 0">
      <div
        v-for="todo in todos"
        :key="todo.id"
        class="d-flex bg-grey text-dark-500 p-2 mb-2"
        :class="{
          'bg-danger text-white': todo.isCompleted === true,
        }"
      >
        <b-form-checkbox @change="markAsCompleted(todo)"
          >&nbsp;
          <del v-if="todo.isCompleted"> {{ todo.title }}</del>
          <span v-else> {{ todo.title }}</span>
        </b-form-checkbox>
      </div>
    </section>

    <section v-else class="m-5">
      <h1 class="display-1">🤽</h1>
      <h5>Your todo list is empty</h5>
    </section>
  </div>
</template>

<script>
export default {
  props: {
    todos: {
      type: Array,
      required: true,
    },
  },
  methods: {
    markAsCompleted(todo) {
      if (!todo.id) {
        return;
      }
      todo.isCompleted = !todo.isCompleted;
    },
  },
};
</script>

<style scoped>
.bg-grey {
  background: rgb(194, 192, 192);
}
</style>
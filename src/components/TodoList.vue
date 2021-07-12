<template>
  <div>
    <div
      v-for="todo in todos"
      :key="todo.id"
      class="d-flex bg-grey text-dark-500 p-2 mb-2"
    >
      <b-form-checkbox value="orange"
        >&nbsp;
        <del v-if="!todo.isCompleted"> {{ todo.title }}</del>
        <span v-else> {{ todo.title }}</span>
        </b-form-checkbox
      >
    </div>
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
};
</script>

<style scoped>
.bg-grey {
  background: rgb(194, 192, 192);
}
</style>
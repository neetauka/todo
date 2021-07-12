<template>
  <div class="m-2">
    <b-tabs pills content-class="mt-3">
      <b-tab title="All" active>
        <div>
          <TodoList :todos="todos" />
        </div>
      </b-tab>
      <b-tab title="Active">
        <div>
          <TodoList :todos="activeTodos" />
        </div>
      </b-tab>
      <b-tab title="Completed">
        <div>
          <TodoList :todos="completedTodos" />
        </div>
      </b-tab>
    </b-tabs>
  </div>
</template>

<script>
// @ is an alias to /src
import TodoList from "@/components/TodoList.vue";
export default {
  name: "Home",
  components: { TodoList },
  computed: {
    activeTodos() {
      return this.todos.filter((todo) => todo.isCompleted === true);
    },
    completedTodos() {
      return this.todos.filter((todo) => todo.isCompleted === false);
    },
  },
  data() {
    return {
      todos: [
        {
          title: "feed the cat",
          id: 18,
          isCompleted: true,
        },
        {
          title: "wash my clothes",
          id: 19,
          isCompleted: false,
        },
        {
          title: "go to the market",
          id: 20,
          isCompleted: true,
        },
        {
          title: "take my bath",
          id: 21,
          isCompleted: false,
        },
        {
          title: "go to school",
          id: 22,
          isCompleted: false,
        },
      ],
    };
  },
};
</script>
<template>
  <div class="m-2">
    <b-tabs pills content-class="mt-3">
      <b-tab title="All" active>
        <div>
          <aside class="m-2">
            <b-form-input
              @keyup.enter="addTodo"
              v-model="currentTodo"
              placeholder="Write a todo.."
            ></b-form-input>
          </aside>

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
      return this.todos.filter((todo) => todo.isCompleted === false);
    },
    completedTodos() {
      return this.todos.filter((todo) => todo.isCompleted === true);
    },
  },
  data() {
    return {
      currentTodo: null,
      todos: [],
    };
  },
  methods: {
    /**
     * Generates random numbers for our todo
     */
    generateRandInt() {
      return Math.random().toString(16).substr(10);
    },

    /**
     * Method to delete all todos
     */
    addTodo() {
      if (!this.currentTodo || this.currentTodo === "") {
        return;
      }
      const payload = {
        isCompleted: false,
        id: this.generateRandInt(),
        title: this.currentTodo,
      };
      console.log("ADDING PAYLOAD-> ", payload);
      this.todos.push(payload);
      this.currentTodo = null;
    },
  },
};
</script>
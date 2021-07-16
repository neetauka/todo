<template>
  <div class="m-2">
    <b-tabs pills content-class="mt-3">
      <b-tab title="All" active>
        <div>
          <aside class="m-5">
            <b-form-input
              @keyup.enter="addTodo"
              v-model="currentTodo"
              placeholder="Write a New Task."
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
        <b-button @click.prevent="deleteAll" variant="danger">
          Delete
        </b-button>
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
      if (!this.currentTodo) {
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

    deleteAll() {
      // Method 1
      this.todos = this.todos.filter((t) => t.isCompleted == false);

      // Method 2
      // this.todos.forEach((todo) => {
      //   if (todo.isCompleted) {
      //     const todoIndex = this.todos.findIndex((x) => x.id === todo.id);
      //     if (todoIndex > -1) {
      //       this.todos.splice(todoIndex, 1);
      //     }
      //   }
      // });
    },
  },
};
</script>
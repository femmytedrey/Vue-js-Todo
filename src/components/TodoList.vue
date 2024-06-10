<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <p class="display-3">Vue Crash Course</p>
      </div>
    </div>
    <div class="row">
      <p>Add create form</p>
    </div>
    <div class="row">
      <div class="col-12 col-lg-6">
        <ul class="list-group">
          <TodoSingle
            v-for="(todo, index) in todos"
            :key="index"
            :todoString="todo.todoString"
            :completed="todo.completed"
          />
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import TodoSingle from "./TodoSingle.vue";
export default {
  components: {
    TodoSingle,
  },
  data() {
    return {
      todos: [
        { todoString: "Make Vue course", completed: false },
        { todoString: "Brush your teeth", completed: true },
        { todoString: "Time for breakfast", completed: false },
        { todoString: "Make Next js course", completed: true },
      ],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push({
        todoString: newTodo,
        completed: false,
      });
    },
    toggleTodo(todo) {
      todo.completed = !todo.completed;
    },
    editTodo(todo, newTodoString) {
      todo.todoString = newTodoString;
    },
    deleteTodo(deleteTodo) {
      this.todo = this.todos.filter(
        (todo) => todo.todoString !== deleteTodo.todoString
      );
    },
  },
};
</script>

<style></style>

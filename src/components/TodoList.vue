<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <p class="display-3">Vue Todo List</p>
      </div>
    </div>
    <div class="row pb-4">
      <NewTodo @on-addTodo="addTodo($event)" />
    </div>
    <div class="row">
      <div class="col-12 col-lg-6">
        <ul class="list-group">
          <TodoSingle
            v-for="(todo, index) in todos"
            :key="index"
            :todoString="todo.todoString"
            :completed="todo.completed"
            @on-delete="deleteTodo(todo)"
            @on-toggle="toggleTodo(todo)"
            @on-edit="editTodo(todo, $event)"
          />
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import TodoSingle from "./TodoSingle.vue";
import NewTodo from './NewTodo.vue'
export default {
  components: {
    TodoSingle,
    NewTodo
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
      this.todos = this.todos.filter(
        (todo) => todo.todoString !== deleteTodo.todoString
      );
    },
  },
};
</script>

<style></style>

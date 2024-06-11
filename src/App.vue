<template>
  <div>
    <TodoList />
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
export default {
  name: "App",
  components: {
    TodoList,
  },
};
</script>

<style>
body {
  background: rgb(66, 66, 66);
  color: aliceblue;
}
</style>

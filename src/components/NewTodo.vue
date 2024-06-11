<template>
  <form @submit.prevent="addTodo" class="col-12 col-lg-6">
    <div class="form-group">
      <input 
        v-model="newTodo" 
        type="text" 
        :class="{'is-invalid':errorMsg}"
        class="form-control" 
        placeholder="Enter a new todo"
      />
      <div v-if="errorMsg" class="text-danger">
        {{ errorMsg }}
      </div>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "",
      errorMsg: "",
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.length > 1) {
        this.$emit("on-addTodo", this.newTodo);
        this.errorMsg = "";
        this.newTodo = "";
      } else {
        this.errorMsg = "Must be more than 1 character";
      }
    },
  },
};
</script>

<style scoped></style>

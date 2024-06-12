<template>
  <li class="d-flex align-items-center list-group-item gap-2">
    <button
      v-if="!isEditing"
      @dblclick="startEditing()"
      :class="{ 'text-decoration-line-through': completed }"
      @click="$emit('on-toggle')"
      class="btn border-0 text-left flex-grow-1"
    >
      {{ todoString }}
    </button>
    <form v-else @submit.prevent="endEditing()" class="flex-grow-1">
      <input
        @blur="startEditing()"
        v-model="newTodoString"
        type="text"
        :class="{ 'is-invalid': checkValid }"
        class="form-control"
      />
    </form>
    <button @click="startEditing()" class="btn btn-outline-primary">
      Edit
    </button>
    <button @click="$emit('on-delete')" class="btn btn-outline-danger">
      Delete
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todoString: String,
    completed: Boolean,
  },
  data() {
    return {
      isEditing: false,
      newTodoString: "",
      checkValid: false,
    };
  },
  methods: {
    startEditing() {
      if (!this.isEditing) {
        this.newTodoString = this.todoString;
        this.isEditing = true;
      } else {
        this.endEditing();
      }
    },
    endEditing() {
      if (this.newTodoString === this.todoString) {
        alert("You have not make any chages");
        this.checkValid = true;
      } else if (this.completed) {
        alert(
          "You can not edit a completed task, click edit again to make your changes"
        );
        this.isEditing = false;
      } else {
        this.isEditing = false;
        this.$emit("on-edit", this.newTodoString);
      }
    },
  },
};
</script>

<style scoped>
/* .completed{
    text-decoration: line-through;
} */
</style>

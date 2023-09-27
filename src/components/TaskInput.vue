<template>
  <div class="task-input">
    <input v-model="newTask" placeholder="Add a new task" @keydown.enter="addTask" />
    <button @click="addTask">Add</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: ''
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== '') {
        this.$emit('add-task', { text: this.newTask, completed: false });
        this.newTask = '';
      }
    }
  }
};
</script>

<style scoped>
/* Add responsive styles as needed */
.task-input {
  margin: 10px 0;
}

input {
  padding: 5px;
  margin-right: 10px;
}

button {
  padding: 5px 10px;
  background-color: #007BFF;
  color: #fff;
  border: none;
  cursor: pointer;
}
</style>

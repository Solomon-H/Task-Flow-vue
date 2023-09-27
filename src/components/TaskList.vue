<template>
  <div class="task-list">
    <ul>
      <li v-for="(task, index) in tasks" :key="index" :class="{ completed: task.completed }">
        <span>{{ task.text }}</span>
        <button @click="deleteTask(index)">Delete</button>
        <button @click="completeTask(index)" v-if="!task.completed">Complete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['tasks'],
  methods: {
    deleteTask(index) {
      this.$emit('delete-task', index);
    },
    completeTask(index) {
      this.$emit('complete-task', index);
    }
  }
};
</script>

<style scoped>
/* Add responsive styles as needed */
.task-list {
  width: 100%;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin: 5px 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.completed {
  text-decoration: line-through;
}
</style>

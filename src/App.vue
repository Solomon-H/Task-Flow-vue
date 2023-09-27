<template>
  <div id="app">
    <h1 class="app-title">Task Manager</h1>
    <div class="content">
      <TaskList :tasks="tasks" @delete-task="deleteTask" @complete-task="completeTask" />
      <TaskInput @add-task="addTask" />
    </div>
  </div>
</template>

<script>
import TaskList from './components/TaskList.vue';
import TaskInput from './components/TaskInput.vue';

export default {
  components: {
    TaskList,
    TaskInput
  },
  data() {
    return {
      tasks: []
    };
  },
  methods: {
    addTask(newTask) {
      this.tasks.push(newTask);
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    completeTask(index) {
      this.tasks[index].completed = true;
    }
  }
};
</script>

<style scoped>
/* Center the title and add a shadow */
.app-title {
  text-align: center;
  padding: 20px;
  background-color: #007BFF;
  color: #fff;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
  margin: 0;
}

/* Add attractive styles to the content */
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

/* Style the input and buttons attractively */
.task-input input {
  padding: 10px;
  border: none;
  border-bottom: 2px solid #007BFF;
  margin-right: 10px;
  font-size: 16px;
  outline: none;
}

.task-input button {
  padding: 10px 20px;
  background-color: #007BFF;
  color: #fff;
  border: none;
  cursor: pointer;
  font-size: 16px;
}

/* Style the task list attractively */
.task-list {
  width: 100%;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin: 10px 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #f0f0f0;
  border-radius: 5px;
  padding: 10px;
}

.completed {
  text-decoration: line-through;
  color: #888;
}
</style>

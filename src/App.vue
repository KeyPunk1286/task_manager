<template>
  <task-manager :tasksData="tasksList" :workersData="workersList" />
</template>

<script>
import TaskManager from "./components/TaskManager.vue";
import { workersList, tasksList } from "./constants/6_tasks_devider";
export default {
  name: "App",
  components: {
    TaskManager,
  },
  data() {
    return {
      workersList,
      tasksList,
    };
  },
};
</script>

<style></style>

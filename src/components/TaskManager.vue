<template>
  <div>
    <task-selector
      :tasksList="tasksData"
      :workersList="workersData"
      @selected="onTaskSelected"
    />
    <worker-list
      v-for="workerData in selectedTasksList"
      :key="workerData.workerId"
      :workerData="getWorkerById(workerData.workerId)"
      :workerTasksData="getTasksByIdList(workerData.tasks)"
    />
  </div>
</template>

<script>
import TaskSelector from "./TaskSelector.vue";
import WorkerList from "./WorkerList.vue";
export default {
  name: "TaskManager",
  components: {
    TaskSelector,
    WorkerList,
  },
  props: {
    tasksData: {
      type: Array,
      required: true,
    },
    workersData: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      selectedTasksList: [
        {
          workerId: 5,
          tasks: [1, 3],
        },
        {
          workerId: 1,
          tasks: [2, 4],
        },
      ],
    };
  },
  methods: {
    getWorkerById(id) {
      return this.workersData.find((worker) => worker.id === id);
    },
    getTasksByIdList(taskIdList) {
      return this.tasksData.filter((task) => taskIdList.includes(task.id));
    },
    onTaskSelected() {
      console.log('onTaskSelected');
    }
  },
};
</script>

<style lang="scss" scoped></style>

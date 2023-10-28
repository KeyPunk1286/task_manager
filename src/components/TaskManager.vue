<template>
  <div>
    <task-selector
      :tasksList="tasksData"
      :workersList="workersData"
      @selected="onTaskSelected"
    />
    <woker-list
      v-for="wokerData in selectedTasksList"
      :key="wokerData.workerId"
      :workerData="getWokerById(wokerData.workerId)"
      :wokerTasksData="getTasksByIdList(wokerData.tasks)"
    />
  </div>
</template>

<script>
import TaskSelector from "./TaskSelector.vue";
import WokerList from "./WokerList.vue";
export default {
  name: "TaskManager",
  components: {
    TaskSelector,
    WokerList,
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
    getWokerById(id) {
      return this.workersData.find((woker) => woker.id === id);
    },
    getTasksByIdList(taskIdList) {
      return this.tasksData.filter((task) => taskIdList.includes(task.id));
    },
    // onTaskSelected(selectedData) {

    // }
  },
};
</script>

<style lang="scss" scoped></style>

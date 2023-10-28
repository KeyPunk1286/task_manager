<template>
  <div>
    <h2>Розподілювач задач</h2>
    <h3>Задачі:</h3>
    <task-selector-item
      v-for="task in tasksList"
      :key="task.id"
      :task="task"
      :workerList="workersList"
      @selected="onSelected($event, task.id)"
    />
  </div>
</template>

<script>
import TaskSelectorItem from "./TaskSelectorItem.vue";
export default {
  components: {
    TaskSelectorItem,
  },
  name: "TaskSelector",
  props: {
    workersList: {
      type: Array,
      required: true,
    },
    tasksList: {
      type: Array,
      required: true,
    },
  },
  methods: {
    onSelected(workerId, taskId) {
      this.$emit("selected", {
        taskId: taskId,
        workerId: workerId,
      });
    },
  },
};
</script>

<style lang="scss" scoped></style>

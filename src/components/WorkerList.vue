<template>
  <div class="parent__list">
    <div class="list__name-worker">{{ workerData.name }}</div>
    <worker-task-item
      v-for="task in workerTasksData"
      :key="task.id"
      :task="task"
      @deleteTask="$emit('deleteTask', task.id)"
    />
  </div>
</template>

<script>
import WorkerTaskItem from "@/components/WorkerTaskItem.vue";
export default {
  name: "WorkerList",
  components: {
    WorkerTaskItem,
  },
  props: {
    workerData: {
      type: Object,
      required: true,
    },
    workerTasksData: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style lang="css" scoped>
.parent__list {
  max-width: 350px;
  border: 1px black solid;
  padding: 5px;
}
.list__name-worker {
  padding: 10px;
  border-bottom: 3px black solid;
  margin-bottom: 10px;
}
</style>

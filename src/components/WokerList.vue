<template>
  <div class="parent__list">
    <div class="list__name-worker">{{ wokerData.name }}</div>
    <woker-task-item
      v-for="task in wokerTasksData"
      :key="task.id"
      :task="task"
      @deleteTask="$emit('deleteTask', task.id)"
    />
  </div>
</template>

<script>
import WokerTaskItem from "./WokerTaskItem.vue";
export default {
  name: "WokerList",
  components: {
    WokerTaskItem,
  },
  props: {
    wokerData: {
      type: Object,
      required: true,
    },
    wokerTasksData: {
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

<template>
  <div class="parent__task-box">
    <div>{{ task.title }}</div>
    <button @click="$emit('deleteTask')">X</button>
  </div>
</template>

<script>
export default {
  name: "WorkerTaskItem",
  props: {
    task: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="css" scoped>
.parent__task-box {
  display: flex;
  justify-content: space-between;
  padding: 10px;
  border: 1px black solid;
  border-radius: 5px;
  max-width: 100%;
}
</style>

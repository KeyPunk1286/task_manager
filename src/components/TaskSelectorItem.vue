<template>
  <div class="paren__box">
    <div class="box-parent__task">
      {{ task.title }}
    </div>
    <div class="box-parent__select-workers">
      <select v-model="selectWorkers">
        <option
          v-for="worker in workerList"
          :key="worker.id"
          :value="worker.id"
        >
          {{ worker.name }}
        </option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: "TaskSelectorItem",
  props: {
    task: {
      type: Object,
      required: true,
    },
    workerList: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      selectWorkersValue: null,
    };
  },
  computed: {
    selectWorkers: {
      get() {
        return this.selectWorkersValue;
      },
      set(workerId) {
        this.selectWorkersValue = workerId;
        this.$emit("selected", workerId);
      },
    },
  },
};
</script>

<style lang="css" scoped>
.paren__box {
  display: flex;
  justify-content: space-between;
  max-width: 500px;
  border: 1px black solid;
  padding: 10px;
}
</style>

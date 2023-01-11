<template>
  <div v-for="item in data" :key="item.id">
    <SingleTask
      @toggle-reminder="$emit('toggle-reminder', item.id)"
      @delete-task="$emit('delete-task', item.id)"
      :task="item"
    />
  </div>
</template>

<script>
import SingleTask from "./SingleTask.vue";

export default {
  name: "TaskPage",
  props: {
    data: Array,
  },
  components: {
    SingleTask,
  },
  emits: ["delete-task", "toggle-reminder"],
};
</script>

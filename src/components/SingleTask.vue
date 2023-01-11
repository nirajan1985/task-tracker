<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h3>
      {{ task.text }}
      <i
        @click="$emit('delete-task', task.id)"
        class="fa-sharp fa-solid fa-xmark"
      ></i>
    </h3>

    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: "SingleTask",
  props: {
    task: Object,
  },
  methods: {
    onDelete(id) {
      this.$emit("delete-task", id);
    },
  },
};
</script>

<style scoped>
.task {
  background-color: #f0eaea;
  margin-bottom: 5px;
  padding: 10px;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 5px;
}
.fa-sharp {
  color: red;
}
.reminder {
  border-left: 5px solid green;
}
</style>

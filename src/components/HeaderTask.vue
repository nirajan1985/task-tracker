<template>
  <header>
    <h1>{{ title }}</h1>
    <ButtonAdd
      @btn-click="$emit('toggle-addtask')"
      :text="showAddTask ? 'Close' : 'Add Task'"
      :color="showAddTask ? 'red' : 'green'"
    />
  </header>
</template>

<script>
import ButtonAdd from "./ButtonAdd.vue";

export default {
  name: "HeaderTask",
  props: {
    title: String,
    showAddTask: Boolean,
  },
  components: {
    ButtonAdd,
  },
};
</script>

<style>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>

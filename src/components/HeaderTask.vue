<template>
  <header>
    <h1>{{ title }}</h1>
    <ButtonAdd text="Add Task" color="green" />
  </header>
</template>

<script>
import ButtonAdd from "./ButtonAdd.vue";

export default {
  name: "HeaderTask",
  props: {
    title: String,
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

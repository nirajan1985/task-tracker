<template>
  <div class="container">
    <HeaderTask
      @toggle-addtask="toggleAddTask"
      title="Task Tracker"
      :showAddTask="showAddTask"
    />
    <div v-show="showAddTask"><AddTask @add-task="addTask" /></div>

    <TaskPage
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :data="tasks"
    />
  </div>
</template>

<script>
import HeaderTask from "./components/HeaderTask.vue";
import TaskPage from "./components/TaskPage.vue";
import AddTask from "./components/AddTask.vue";
export default {
  name: "App",
  components: {
    HeaderTask,
    TaskPage,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask];
    },
    deleteTask(id) {
      if (confirm("Are you sure you want to delete ?")) {
        this.tasks = this.tasks.filter((item) => item.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((item) =>
        item.id === id ? { ...item, reminder: !item.reminder } : item
      );
    },
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
  },

  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctors Appointment",
        day: "March 1st at 2:30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Meeting at school",
        day: "March 3rd at 1:30pm",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>

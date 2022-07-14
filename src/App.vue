<template>
  <h4>My tasks</h4>
  <div class="tasks">
    <div
      class="task"
      :class="{ completed: task.isCompleted }"
      v-for="task in tasks"
      :key="task._id"
      @click="completedHandler(task._id)"
    >
      <div
        class="round"
        :class="{
          business: task.type === 'business',
          personal: task.type === 'personal',
        }"
      ></div>
      <span>{{ task.name }}</span>
    </div>
  </div>
  <div class="add-task">
    <input type="text" placeholder="Type your task" v-model='taskName'/>
    <button @click="addTask">+</button>
  </div>
</template>



<script>
import { uuid } from 'vue3-uuid';

export default {
  name: "App",
  data() {
    return {
      taskName: '',
      tasks: [
        {
          _id: uuid.v4(),
          name: "Create todo app",
          isCompleted: true,
          type: "personal",
        },
        {
          _id: uuid.v4(),
          name: "Create messenger",
          isCompleted: false,
          type: "business",
        },
        {
          _id: uuid.v4(),
          name: "To do tests",
          isCompleted: true,
          type: "business",
        },
        {
          _id: uuid.v4(),
          name: "Auth",
          isCompleted: false,
          type: "business",
        },
        {
          _id: uuid.v4(),
          name: "Styles",
          isCompleted: true,
          type: "business",
        },
      ],
    };
  },
  methods: {
    completedHandler: function (taskId) {
      this.tasks.map((t) =>
        t._id === taskId ? (t.isCompleted = !t.isCompleted) : t
      );
    },
    addTask: function () {
        console.log(this.taskName)
        const newTask = {
          _id: uuid.v4(),
          name: this.taskName,
          isCompleted: false,
          type: "personal",
        }
        this.tasks.push(newTask)
    }
  },
};
</script>

<style>
</style>

<template>
  <div class="container">
    <h4>My tasks</h4>
    <div class="wrapper-stat">
      <div class="stat">
        <h5>Business</h5>
        <div class="wrapper-progress">
          <div class="bar" :style='{width: `${statistic.business}`}'></div>
        </div>
      </div>
      <div class="stat">
        <h5>Personal</h5>
        <div class="wrapper-progress">
          <div class="bar personal" :style='{width: `${statistic.personal}`}'></div>
        </div>
      </div>
    </div>
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
        <div class="delete-task" @click="removeTask(task._id)">
          <img src="../src/assets/trash.png" alt="">
        </div>
      </div>
    </div>
    <div class="add-task">
      <input
          type="text"
          placeholder="Type your task"
          v-model='taskName'
          v-on:keyup.enter="addTask"
      />
      <button @click="addTask">+</button>
    </div>
  </div>

</template>


<script>
import {uuid} from 'vue3-uuid';

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
      const newTask = {
        _id: uuid.v4(),
        name: this.taskName,
        isCompleted: false,
        type: "personal",
      }
      this.tasks.push(newTask)
      this.taskName = ''
    },
    removeTask: function (taskId) {
      this.tasks = this.tasks.filter(t => t._id !== taskId)
    }
  },
  computed: {

    statistic: function() {
      const count = this.tasks.length || 1
      const businessData = this.tasks.filter(t => t.type === 'business')
      const personalData = this.tasks.filter(t => t.type === 'personal')
      return {
        business: Math.round((businessData.length * 100) / count) + '%',
        personal: Math.round((personalData.length * 100) / count) + '%',
      }
    }
  }
};
</script>

<style>
</style>

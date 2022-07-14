<template>
  <h4>My tasks</h4>
  <div class="tasks">
    <div
        class='task'
        :class='{completed: task.isCompleted}'
        v-for="task in tasks"
        :key="task._id">

      <div
          class='round'
          :class="{
            business: task.type === 'business',
            personal: task.type === 'personal',
                  }"
      ></div>
      <span>{{ task.name }}</span>

    </div>
  </div>
  <div class='add-task'>
    <input type="text" placeholder='Type your task'>
    <button>+</button>
  </div>

</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      tasks: [
        {
          _id: 'ksefklk3f2331f',
          name: 'Create todo app',
          isCompleted: true,
          type: 'personal'
        },
        {
          _id: 'ksefkl43tk3f2331f',
          name: 'Create messenger',
          isCompleted: false,
          type: 'business'
        },
        {
          _id: '3fklk3f2331f',
          name: 'To do tests',
          isCompleted: true,
          type: 'business'
        },
        {
          _id: '657efklk3f2331f',
          name: 'Auth',
          isCompleted: false,
          type: 'business'
        },
        {
          _id: 'ksefklk3f237631f',
          name: 'Styles',
          isCompleted: true,
          type: 'business'
        },
      ]
    }
  }
}
</script>

<style>
</style>

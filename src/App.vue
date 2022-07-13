<template>
  <h4>My tasks</h4>
  <div class="tasks">
    <div class='task completed'>
      <div class="round checked">
        <div class="checkbox"></div>
      </div>
      <span>Create app VueJS</span>
    </div>
  </div>
  <div class='add-task'>
    <input type="text" placeholder='Type your task'>
    <button>+</button>
  </div>

</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'




export default {
  name: 'App',
  data() {
    return {
      tasks: [
        {
          _id: 'ksefklk3f2331f',
          name: 'Create todo app',
          isCompleted: false,
          type: 'business'
        }

      ]
    }
  }
}
</script>

<style>
</style>

<script>
export default {
  name: 'App',
  data(){
    return {
      tasks: [
        {
          text: 'Learn HTML',
          done: true
        },
        {
          text: 'Learn CSS',
          done: true
        },
        {
          text: 'Learn Vue',
          done: false
        }
      ]
    }
  }
}
</script>

<template>
  <h1>Todo List</h1>
  <ul>
    <li v-for="task in tasks">
      {{ task.text }}
    </li>
  </ul>
</template>

<style>

</style>

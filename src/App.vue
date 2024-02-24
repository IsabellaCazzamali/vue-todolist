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

    <!-- Stampa un item per ogni todo -->
    <li v-for="task in tasks">
      <!-- Aggiunge testo sbarrato quando true -->
      <span :style="{textDecoration: task.done ? 'line-through' : '' }">
        {{ task.text }}
      </span>
      
    </li>
  </ul>
</template>

<style>

</style>

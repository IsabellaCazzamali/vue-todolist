<script>
export default {
  name: 'App',
  data(){
    return {
      newTask: '',
      error: false,
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
          text: 'Learn JS',
          done: false
        },
        {
          text: 'Learn Vue',
          done: false
        },
        {
          text: 'Learn PHP',
          done: false
        },
        {
          text: 'Learn Laravel',
          done: false
        }
      ]
    }
  },
  methods: {
    // rimuove task al click
    removeTask(index){
      console.log('rimuovi questa task', index);
      this.tasks.splice(index, 1);
    },
    /* Method (a function inside an object) syntax ES6 */
    // Aggiunge la nuova task che scriviamo nell'input
    addTask(){
      console.log('add this task', this.newTask);
      if(this.newTask.length > 4) {
        // Crea un nuovo oggetto per la task da aggiungere
        const obj = {
          text: this.newTask,
          done: false
        };
        // Agisce sull'oggetto creato aggiungendo una nuova task
        this.tasks.unshift(obj);
        this.newTask = '';
      } else {
        this.error = 'The task must be at least 5 characters long';
      }
    },
    // Cambia lo stato della task
    toggle(index){
      this.tasks[index].done = !this.tasks[index].done;
    }
  }
}
</script>

<template>
  <div class="container my-4">
    <div class="card p-3">
      <h2>Todo List</h2>

      <!-- Input per aggiunger nuova task -->
      <div class="input-group mb-3">
        <input type="text" v-model="newTask" @keyup.enter="addTask">
        <button class="btn btn-dark" @click="addTask">Add</button>
      </div>

      <span class="text-danger" v-if="error">{{ error }}</span>

        <ul class="list-group" v-if="tasks.length > 0">

          <!-- Stampa un item per ogni todo -->
          <li v-for="(task, index) in tasks" class="list-group-item d-flex justify-content-between">
          <!-- Aggiunge testo sbarrato quando true / Option 1 con style binding + evento al click -->
            <span :style="{textDecoration: task.done ? 'line-through' : '' }" @click="toggle(index)">
              {{ task.text }}
            </span>
            <span v-on:click="removeTask(index)">
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-x-circle" viewBox="0 0 16 16">
              <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14m0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16"/>
              <path d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708"/>
              </svg>
            </span>

            <!-- Option 2 con class binding 
            <span v-bind:class="{'text-decoration-line-through': task.done }">
              {{ task.text }}
            </span> -->
      
          </li>
        </ul>
        <p v-else>
          Nothing left to do! Enjoy your day!
        </p>
      
    </div>
  </div>

</template>

<style>

</style>

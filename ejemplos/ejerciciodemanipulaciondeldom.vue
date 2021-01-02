<template>
  <div id="app">
    <h2>Administrador de Tareas</h2>
    <h3>{{ name }}</h3>

    <fieldset>
      <legend>Nueva Tarea</legend>
      <p><input type="text" placeholder="Titulo" v-model="newTask.title" /></p>
      <p>
        <input
          type="number"
          placeholder="Horas Trabajadas"
          v-model="newTask.time"
        />
      </p>
      <p>
        <button @click="addTask">Guardar</button>
        <button @click="cancel">Cancelar</button>
      </p>
    </fieldset>

    <div>
      <h3>Lista Tareas</h3>
      <p style="color: tomato" v-show="!tasks.length">
        Aun no hay tareas cargadas
      </p>
      <div style="display: none" v-show="tasks.length">
        <ol>
          <li v-for="(t, i) in tasks" :key="t">
            <span>{{ t.title }} - {{ t.time }}</span>
            <span @click="removeTask(i)"> ❌</span>
          </li>
        </ol>
        <hr />
        <p>
          Tiempo Trabajado:<strong>{{ totalTime }}</strong>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  el: '#app',

  data () {
    return {
      name: 'Ignacio Anaya',
      tasks: [],

      newTask: {
        title: '',
        time: 0
      }
    }
  },

  created () {
    this.tasks = JSON.parse(localStorage.getItem('tasks')) || []
  },

  computed: {
    totalTime () {
      if (!this.tasks.length) {
        return 0
      }

      let total = 0

      this.tasks.forEach(t => {
        total += parseInt(t.time)
      })

      return total
    }
  },

  methods: {
    addTask () {
      if (!this.newTask.title || !this.newTask.time) {
        return
      }

      this.tasks.push({
        title: this.newTask.title,
        time: this.newTask.time
      })

      localStorage.setItem('tasks', JSON.stringify(this.tasks))

      this.newTask.title = ''
      this.newTask.time = 0
    },

    removeTask (index) {
      this.tasks.splice(index, 1)
      localStorage.setItem('tasks', JSON.stringify(this.tasks))
    },

    cancel () {
      this.newTask.title = ''
      this.newTask.time = 0
    }
  }
}
</script>

<style lang="scss">
@import "./scss/main.scss";

.results {
  margin-top: 50px
}
</style>

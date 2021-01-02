<template>
  <div>
    <h1>Este es un component hijo</h1>
    <local-component></local-component>
    <localComponent></localComponent>
    <button @click="addProp">Agregar</button>

    <p>{{ person }}</p>
  </div>
</template>

<script>
// Se crea el objeto vue (todos los componentes devuelven un objeto)
export default {
  data () {
    return {
      person: {
        name: 'carlos'
      }
    }
  },
  methods: {
    addProp () {
      // this.person.lastName = 'ruales' //MANERA INCORRECTA, NO QUEDA REACTIVO
      // this.$set(this.person,'lastName','ruales') //PARA AGREGAR UNO
      this.person = Object.assign({}, this.person, { a: 1, b: 2 }) // Cuando se necesitan agregar varios campos dinamicamente
    }
  }
}
</script>

// Al mutar/cambiar una propiedad de un objeto dentro de data, este si cambia pero el watcher nunca se entera de ese cambio por lo tanto no se ve reflejado en la página (no hay reactividad). Hay dos soluciones.

// La de vue

// // $set es una función del framework

// // this.$set(<objeto a agregar una propiedad>, <nombre de la propiedad>, <valor de esa propiedad>)

// this.$set(this.person, 'lastName', 'Anaya')
// La de ES6

// // Esto va a crear un objeto nuevo y se va a asignar al objeto deseado. agregando lo que hacia falta

// // this.person = Object.assign({}, <Objeto que quiero mezclar> , { <Que se va a incorporar> })

// this.person = Object.assign({}, this.person, { a: 1, b: 2 })

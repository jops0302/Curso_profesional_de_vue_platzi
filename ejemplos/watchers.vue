<template>
  <div id="app">
    <input v-model="name">
    <input v-model="lastName">
    <p>{{ fullName }}</p>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      name: '',
      lastName: ''
    }
  },
  computed: {
    fullName () {
      // return this.name + ' ' + this.lastName
      // se puede utilizar cualquieta de la dos formas la de abajo se llama template string
      return `${this.name} ${this.lastName}`
    }
  },

  watch: {
    name (newVal, oldVal) {
      console.log(newVal, oldVal)
    }
  }
}
</script>

<style lang="scss">
@import './scss/main.scss'
</style>

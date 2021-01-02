<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <p>{{ 1 + 2 }}</p>
    <p>{{ 'hola' + 'mundo' }}</p>
    <p>{{ person.name }}</p>
    <p>{{ person.name.toUpperCase() }}</p>
    <p>{{ JSON.stringify(person) }}</p>
    <p>{{ true ? 'true' : 'false' }}</p>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Hola Vue!',

      person: {
        name: 'jose'
      }
    }
  }
}
</script>

<style lang="scss">
@import './scss/main.scss'
</style>

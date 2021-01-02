<template>
  <div id="app">
    <p v-show="showValue">{{ value }}</p>

    <p v-if="showValue">{{ value }}</p>
    <p v-else>{{ 'algo mas' }}</p>

   <ul id="example-1">
  <li v-for="i in items" :key="i">
    {{ i }}
  </li>
</ul>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Hola Vue!',

      showValue: true,
      value: 'Algo',

      items: [
        1,
        2,
        3,
        4,
        5,
        6,
        7,
        8,
        9
      ]
    }
  }
}
</script>

<style lang="scss">
@import './scss/main.scss'
</style>

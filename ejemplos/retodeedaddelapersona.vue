<template lang="pug">
  #app
    .container
      .field
        label(class="label") Seleccione su fecha de nacimiento
        .control
          input(v-model="birthday" class="input" type="date")
      p(v-show="!isNaN(getYears)") Su edad es:
        strong {{ getYears }}
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      birthday: ''
    }
  },
  computed: {
    getYears () {
      const year = new Date().getFullYear()
      const birthday = new Date(this.birthday).getFullYear()
      return year - birthday
    }
  }
}
</script>

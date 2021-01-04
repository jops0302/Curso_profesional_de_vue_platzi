<template>
   <section class="hero is-success">
       <div class="hero-head">
           <header class="navbar">
               <div class="container">
                   <div class="navbar-start">
                       <div class="navbar-item">
                           <strong>
                               🥅 Platzi Music
                           </strong>
                       </div>
                   </div>
                   <div class="navbar-end navbar-menu">
                       <a @click="selectLang('en')" class="navbar-item">Ingles</a>
                       <a @click="selectLang('es')" class="navbar-item">Español</a>
                       <router-link class="navbar-item" to="search">{{ $t('search') }}</router-link>
                       <router-link class="navbar-item" to="about">{{ $t('about') }}</router-link>
                   </div>
               </div>
           </header>
       </div>
       <div class="hero-body">
           <div class="container has-text-centered">
               <h1 class="title">Platzi Music</h1>
               <h2 class="subtitle">Canciones que estan Vue-nisimas!</h2>
               <pm-player></pm-player>
           </div>
       </div>
   </section>
</template>

<script>
import PmPlayer from '@/components/Player.vue'
export default {
  components: { PmPlayer },

  methods: {
    selectLang (lang) {
      this.$i18n.locale = lang
    }
  }
}
</script>

<template>
  <div id="app">
    <pm-header></pm-header>

    <pm-notification :typeNotification="hasData" v-show="showNotification">
      <p v-if="hasData" slot="body">No se encontraron resultadosddddd</p>
      <p v-else slot="body">{{ searchMessage }}</p>
    </pm-notification>

    <pm-loader v-show="isLoading"></pm-loader>
    <section class="section" v-show="!isLoading">
      <nav class="nav">
        <div class="container is-flex">
          <input type="text" class="input is-large" placeholder="Buscar Canciones" v-model="searchQuery">
          <a class="button is-info is-large" @click="search">Buscar</a>
          <a class="button is-danger is-large">&times;</a>
        </div>
      </nav>
      <div class="container">
      <p><small>{{ searchMessage }}</small></p>
      </div>
      <div class="container results">
        <div class="columns is-multiline">
          <div class="column is-one-quarter" v-for="t in tracks" :key="t">
            <pm-track  :track='t' @select="setSelectedTrack"
            :class="{ 'is-active': t.id === selectedTrack }"></pm-track>
            {{ t.name }} - {{ t.artists[0].name }}
          </div>
        </div>
      </div>
    </section>
    <pm-footer></pm-footer>
  </div>
</template>

<script>
import trackService from '@/services/track'

import PmFooter from '@/components/layout/footer.vue'
import PmHeader from '@/components/layout/header.vue'

import PmTrack from '@/components/Track.vue'

import PmNotification from '@/components/shared/Notification.vue'
import PmLoader from '@/components/shared/Loader.vue'

export default {
  name: 'app',
  components: {
    PmFooter,
    PmHeader,
    PmTrack,
    PmLoader,
    PmNotification
  },
  data () {
    return {
      searchQuery: '',
      tracks: [],

      isLoading: false,
      showNotification: false,

      selectedTrack: '',

      hasData: false
    }
  },

  computed: {
    searchMessage () {
      return `Encontrados: ${this.tracks.length}`
    }
  },

  watch: {
    showNotification () {
      if (this.showNotification) {
        setTimeout(() => {
          this.showNotification = false
        }, 3000)
      }
    }
  },

  methods: {
    search () {
      if (this.searchQuery === '') { return }
      this.isLoading = true
      trackService.search(this.searchQuery)
        .then(res => {
          this.showNotification = true
          this.hasData = res.tracks.total === 0
          this.tracks = res.tracks.items
          this.isLoading = false
        })
    },
    setSelectedTrack (id) {
      this.selectedTrack = id
    }
  }
}
</script>

<style lang="scss">
@import './scss/main.scss';

.results {
  margin-top: 50px;
}
.is-active {
  border: 3px #23d160 solid;
}
</style>

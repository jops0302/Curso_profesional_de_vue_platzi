<template>
  <div class="card" v-if="track && track.album">
      <div class="card-image">
          <figure class="image">
              <img :src="track.album.images[0].url" alt="">
          </figure>
      </div>
      <div class="card-content">
          <div class="media">
              <div class="media-start">
                  <figure class="image is-48x48">
                      <img :src="track.album.images[0].url" alt="">
                  </figure>
              </div>
              <div class="media-content">
                  <p class="title is-6">
                      <strong>{{ track.name }}</strong>
                  </p>
                  <p class="subtitle is-6">{{ track.artists[0].name }}</p>
              </div>
          <div class="content">
              <small>{{ track.duration_ms | ms-to-mm }}</small>
              <nav class="level">
                  <div class="level-start">
                      <button href="" class="level-items button is-primary">
                          <span class="icon is-small" @click.prevent="selectTrack">▶️</span>
                      </button>
                      <button href="" class="level-items button is-warning">
                          <span class="icon is-small" @click.prevent="goToTrack(track.id)">🌐</span>
                      </button>
                  </div>
              </nav>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
import trackMixin from '@/mixins/track'
export default {
  mixins: [trackMixin],

  props: {
    track: { type: Object, required: true }
  },

  methods: {
    goToTrack (id) {
      if (!this.track.preview_url) { return }

      this.$router.push({ name: 'track', params: { id } })
    }
  }
}
</script>

<style>

</style>

<template>
  <div class="card">
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
          </div>
          <div class="content">
              <small>{{ track.duration_ms }}</small>
              <nav class="level">
                  <div class="level-start">
                      <a href="" class="level-items">
                          <span class="icon is-small" @click.prevent="selectTrack">▶️</span>
                      </a>
                  </div>
              </nav>
          </div>
      </div>
  </div>
</template>

<script>
export default {
  props: {
    track: { type: Object, required: true }
  },

  methods: {
    selectTrack () {
      this.$emit('select', this.track.id)

      this.$bus.$emit('set-track', this.track)
    }
  }
}
</script>

<style>

</style>

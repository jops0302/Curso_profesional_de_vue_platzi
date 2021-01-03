<template>
<div class="container">
    <div class="columns">
        <div class="column is-3 has-text-centered">
          <figure class="media-end">
            <p class="image">
              <img :src="track.album.images[0].url" alt="">
            </p>
            <p>
              <a href="" class="button is-primary is-large">
                <span class="icon" @click="selectTrack"></span>
              </a>
            </p>
          </figure>
        </div>
        <div class="column is-">
          <div class="panel">
            <div class="panel-heading">
              <h1 class="title">{{ track.name }}</h1>
            </div>
            <div class="panel-block">
              <article class="media">
                <div class="media-content">
                  <div class="content">
                    <ul v-for="(v, k) in track" :key="k">
                      <li>
                        <strong>{{ k }}:&nbsp;</strong>
                        <span>{{ v }}</span>
                      </li>
                    </ul>
                  </div>
                </div>
                <nav class="level">
                  <div class="level-end">
                    <a href="" class="level-item"></a>
                  </div>
                </nav>
              </article>
            </div>
          </div>
        </div>
    </div>
</div>
</template>

<script>
import trackMixin from '@/mixins/track'
import trackService from '@/services/track'

export default {
  mixins: [trackMixin],

  data () {
    return {
      track: {}
    }
  },
  created () {
    const id = this.$route.params.id

    trackService.getById(id)
      .then(res => {
        this.track = res
      })
  }
}
</script>

<style lang="scss" scoped>
    .columns {
        margin: auto;
    }
    .column {
        margin: auto;
    }
</style>

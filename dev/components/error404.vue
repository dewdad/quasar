<template>
  <div class="error-page window-height window-width bg-light column items-center">
    <div class="error-code bg-primary flex items-center justify-center">
      404
    </div>
    <div>
      <div class="error-card card bg-white column items-center justify-center">
        <q-icon class="text-grey-5" name="error_outline" />
        <p class="caption text-center">Oops. Nothing here...</p>
        <p class="text-center group">
          <q-btn v-if="canGoBack" class="grey push small" @click="goBack" icon="keyboard_arrow_left">
            Go back
          </q-btn>
          <router-link to="/">
            <q-btn class="grey push small" iconRight="home">
              Go home
            </q-btn>
          </router-link>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      canGoBack: window.history.length > 1
    }
  },
  methods: {
    goBack () {
      window.history.go(-1)
    }
  }
}
</script>

<style lang="stylus">
.error-page
  .error-code
    height 50vh
    width 100%
    padding-top 15vh
    font-size 30vmax
    color rgba(255, 255, 255, .2)
    overflow hidden
  .error-card
    margin-top -25px
    width 90vw
    max-width 600px
    padding 50px
    i
      font-size 5rem
</style>

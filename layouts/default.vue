<template>
  <v-app dark>
    <v-app-bar
      fixed
      app
    >
      <v-toolbar-title v-text="title" />
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer app>
      <transition name="fade">
        <v-btn
          v-scroll="onScroll"
          v-show="fab"
          fab
          dark
          fixed
          bottom
          right
          color="primary"
          @click="toTop">
          <v-icon class="text-h4 white--text">mdi-chevron-up</v-icon>
        </v-btn>
      </transition>

      <span class="text-lg-right">&copy; {{ new Date().getFullYear() }} Timeconcier Co.Ltd.</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      title: 'Vuetify.js',
      fab: false,
    }
  },
  methods: {
    onScroll (e){
      if (typeof window === 'undefined') return
      const top = window.pageYOffset ||   e.target.scrollTop || 0
      this.fab = top > 500
    },
    toTop () {
      this.$vuetify.goTo(0)
    }
  }
}
</script>


<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: 0.5s;
} 
.fade-enter, .fade-leave-to {
  opacity: 0;
  transform: scale(0);
}
</style>
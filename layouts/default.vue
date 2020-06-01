<template lang="pug">
  v-app
    Navbar
    v-content
      nuxt
    SideLinks
    Footer
</template>

<script>
import Footer from '~/components/Footer.vue'
import Navbar from '~/components/Navbar.vue'
import SideLinks from '~/components/SideLinks.vue'

export default {
  components: {
    Footer,
    Navbar,
    SideLinks
  }
}
</script>

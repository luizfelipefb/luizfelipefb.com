<template lang="pug">
  aside.pa-1.fill-height.aside(:class="asideState")
    Links.column.fill-height.justify-center
</template>

<style lang="sass">
.aside
  position: fixed
  right: 0

  img
    transition: opacity .75s ease

    &:hover
      opacity: 1

.aside--show
  img
    opacity: .25

.aside--hide
  img
    opacity: 0
</style>

<script>
import Links from '~/components/utils/Links.vue'
export default {
  components: {
    Links
  },
  data() {
    return {
      show_side_links: true
    }
  },
  computed: {
    asideState() {
      return this.show_side_links ? 'aside--show' : 'aside--hide'
    }
  },
  beforeMount() {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      this.show_side_links = window.scrollY + window.innerHeight <= window.document.body.scrollHeight - 40
    }
  }
}
</script>

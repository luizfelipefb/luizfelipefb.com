<template lang="pug">
  v-app-bar.v-app-bar--fixed.blue-grey.lighten-5(flat, height="100px", :style="{'opacity': opacity, 'transition': 'opacity 0.75s ease'}")
    v-layout.justify-center
      v-flex.md7.blue-grey--text.text--darken-2
        .display-1.font-weight-black PIN
        v-divider.blue-grey.darken-2
        .body-2 LUIZ FELIPE FONTES BOTELHO
</template>

<script>
export default {
  data() {
    return {
      opacity: 0
    }
  },
  beforeMount() {
    window.addEventListener('scroll', this.handleScroll)
  },
  mounted() {
    this.handleScroll()
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      // get element DOM box from class selector
      const selector = '.myname'
      const elbox = this.$el.parentElement.querySelector(selector).getBoundingClientRect()

      // if the element is half height visible, does not show navbar
      if (elbox.top + elbox.height / 2 > 0) {
        this.opacity = 0
      } else {
        this.opacity = 0.95
      }
    }
  }
}
</script>

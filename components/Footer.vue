<template lang="pug">
  v-footer.blue-grey.darken-4.fixed.aboslute(height="100px")
    v-layout.align-center
      .blue-grey--text.text--darken-3
        a.blue-grey--text.text--darken-3(href="https://en.wikipedia.org/wiki/Pi", target="_blank") π
        span n
      v-spacer
      Links.align-center.justify-end.links
      .separator.blue-grey.darken-3
</template>

<style lang="sass">
footer
  a
    text-decoration: none

  .links
    span
      filter: invert(100%)

    img
      opacity: .25

      &:hover
        opacity: 1

  .separator
    height: 1px
    width: 10vw
</style>

<script>
import Links from '~/components/utils/Links.vue'
export default {
  components: {
    Links
  }
}
</script>

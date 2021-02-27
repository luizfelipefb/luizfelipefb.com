<template lang="pug">
  main
    div.fluid.full-height.blue-grey.lighten-5
      v-layout.align-center.wrap.py-5
        v-flex.offset-xs1.xs10.offset-md1.md5.details
          span.display-2.font-weight-bold.blue-grey--text.text--darken-2.myname PIN
          v-flex.xs12
            span.blue-grey--text.text--darken-2 LUIZ FELIPE FONTES BOTELHO
          .separator.blue-grey.darken-2
          .short
            p 📍 Born, raised and living in brazil since '85
            p 🏢 Currently working as a senior software engineer at <a target="_blank" href="https://ciandt.com">ciandt</a> where I joined in april 2008
            p ❤️ Passionate about health and fitness, nutrition, each and every sport on earth (and maybe out of it, if I ever get the chance)
            p 💪 I'm also a mediocre bodybuilder, trying to get to 212/7%@5'8, missing a few pounds :(
    a.blue-grey--text.text--lighten-3.read(href="#", @click="$vuetify.goTo('.about', {offset: 0})")
      p.ma-0.title Read More
      v-icon.blue-grey--text.text--lighten-3 keyboard_arrow_down

    div.fluid.full-height.blue-grey.darken-4.white--text.about
      v-layout.align-center.justify-center
        v-flex.xs9.md7
          p.pb-5.display-1.font-weight-black ABOUT
          p.pb-5.subheading I am a problem solving oriented person. I like to think that I can overcome challenges even if I don't have the knowledge to do so, but I can learn what ever I need to solve the problem and move to the next one. This is my goal, professionally, and in life one might say, to overcome challenges thrown at me, no matter what. In general, I am very patient and an easy person to deal with. To put it simple, my objective is to get things done. So, how can I help?
          v-layout.body-2.wrap.cards
            v-flex.sm12.md6.lg3
              p.title General
              ul
                li Cloud Computing, Microservices, APIs
                li Google Cloud Platform (GCP)
                li Amazon Web Services (AWS)
                li Microsoft Azure
                li DevOps
                li Infrastructure, NAS, network, VPN, vnet, etc
                li Home Automation
            v-flex.sm12.md6.lg3
              p.title Software Development
              ul
                li Java, Javascript, C#, python, Golang, NodeJS, just to name a few
                li VueJS, React, Redux, AngularJS, Material, Bootstrap, and others, to name some more, but from a different end
                li Fullstack Development
                li Plenty others 2 to 5 combined letters
            v-flex.sm12.md6.lg3
              p.title Community
              ul
                li Open source projects on gihtub
                li GitLab contributor
                li Helper (anyway possible)
                li Writer?
            v-flex.sm12.md6.lg3
              p.title Health and Fitness
              ul
                li Self thought nutrition through online courses and other articles
                li Workout programs designer, lol

    div.fluid.full-height.blue-grey.lighten-5.articles
      v-layout.align-center.justify-center
        v-flex.xs9.md7
          p.pb-5.display-1.font-weight-black PUBLICATIONS
          p.subheading The reason I'm self-proclaimed writer :).
          p.pb-5.subheading These are my latest publications on <a target="_blank" href="https://medium.com/@luizfelipefb">medium</a>, but bear in mind the <strong>self</strong>-proclaimed thing. I'm no writer what so ever, nor english is my first language, but I do my best. Appreciation in the form of claps 👏 is always welcomed. "Like if you like it, dislike if you did, subscribe, check out the link where to buy the stuff feature on and don't forget to click the notifications bell icon"<sup>LTT</sup>.
          .text-center(v-show="articles.length === 0")
            v-progress-circular(:size="70", :width="7", indeterminate)
          v-carousel.blue-grey.lighten-4.articles-list(light, v-show="articles.length > 0", :height="400", :hide-delimiters="$vuetify.breakpoint.mdAndDown")
            v-carousel-item.pa-5(v-for="item in articles", :key="item.url")
              a(:alt="item.title", :href="item.url", target="_blank")
                v-img.mb-3(contain, :src="item.img", max-height="180")
                blockquote.subheading.font-weight-bold {{item.title}}
                blockquote.subheading.font-weight-thin {{item.subtitle}}
</template>

<script>
const htmlToText = require('html-to-text')
const ellipsis = require('text-ellipsis')

export default {
  data() {
    return {
      articles: []
    }
  },
  mounted() {
    this.fetchArticles('luizfelipefb').then((response) => {
      response.items.forEach((post) => {
        const description = htmlToText.fromString(post.description, {
          ignoreHref: true,
          ignoreImage: true
        })
        this.articles.push({
          url: post.link,
          img: post.thumbnail,
          title: post.title,
          subtitle: ellipsis(description, 480),
          tags: post.categories
        })
      })
    })
  },
  methods: {
    fetchArticles(username) {
      const url = `https://api.rss2json.com/v1/api.json?rss_url=https://medium.com/feed/@${username}`
      return this.$axios.$get(url)
    }
  }
}
</script>

<style lang="sass">
.read
  text-align: center
  position: absolute
  left: calc(50% - 49px)
  margin-top: -60px
  text-decoration: none

  a
    text-decoration: none

.full-height
  min-height: 100vh
  display: flex

.details
  letter-spacing: 2px

  .short
    max-width: 90%

  .separator
    height: 7px
    margin: 20px 0px 20px -180px

.about
  padding: 100px 0px

  .cards .flex
    padding: 10px

.articles
  padding: 100px 0px

  .articles-list
    border-radius: 8px

    .v-responsive__content
      padding: 0px 40px

    .v-window__prev, .v-window__next, .v-carousel__controls
      background: transparent

    a
      color: inherit
      text-decoration: none
</style>

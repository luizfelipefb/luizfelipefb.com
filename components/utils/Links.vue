<template lang="pug">
  v-layout
    span.pa-3(v-for="item in links", :key="item.href")
      a(:href="item.href", target="_blank")
        img(:alt="item.alt", height="20", width="20", :src="item.img_src")
</template>

<script>
export default {
  data: () => {
    return {
      links: [
        {
          href: 'mailto:luizfelipefb@gmail.com?subject=3.14n.dev',
          img_src: 'https://unpkg.com/simple-icons@latest/icons/gmail.svg',
          alt: 'mail me'
        },
        {
          href: 'https://github.com/luizfelipefb/',
          img_src: 'https://unpkg.com/simple-icons@latest/icons/github.svg',
          alt: 'me @ github'
        },
        {
          href: 'https://facebook.com/luizfelipefb',
          img_src: 'https://unpkg.com/simple-icons@latest/icons/facebook.svg',
          alt: 'me @ facebook'
        },
        {
          href: 'https://instagram.com/luizfelipefb',
          img_src: 'https://unpkg.com/simple-icons@latest/icons/instagram.svg',
          alt: 'me @ instagram'
        },
        {
          href: 'https://linkedin.com/in/luizfelipefb',
          img_src: 'https://unpkg.com/simple-icons@latest/icons/linkedin.svg',
          alt: 'me @ linkedin'
        },
        {
          href: 'https://twitter.com/luizfelipefb',
          img_src: 'https://unpkg.com/simple-icons@latest/icons/twitter.svg',
          alt: 'me @ twitter'
        }
      ]
    }
  }
}
</script>

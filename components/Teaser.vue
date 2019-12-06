<template>
  <header class="top-header util__flex util__container">
    <nav class="top-header__col">
      <ul class="top-header__nav">
        <li :key="index" v-for="(navitem, index) in $store.state.settings.main_navi">
          <nuxt-link class="top-header__link" :to="navitem.link.cached_url">
            {{ navitem.name }}
          </nuxt-link>
        </li>
      </ul>
    </nav>
    <a href="/" class="top-header__col top-header__logo">
      <img src="//a.storyblok.com/f/42016/1096x313/0353bf6654/logo2.png">
    </a>
    <nav class="top-header__col top-header__second-navi">
      <ul class="top-header__nav top-header__nav--right">
        <li>
          <nuxt-link class="top-header__link" to="/en/blog">English</nuxt-link>
        </li>
        <li>
          <nuxt-link class="top-header__link" to="/de/blog">German</nuxt-link>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  props: ['blok'],

  data () {
    return {
      currentSlide: 0
    }
  },

  computed: {
    slide () {
      let slides = this.blok.body.filter((slide, index) => {
        return this.currentSlide === index
      })
      if (slides.length) {
        return slides[0]
      }
      return null
    }
  },

  methods: {
    handleDotClick (index) {
      this.currentSlide = index
    }
  }
}
</script>

<style lang="scss">
.teaser__pag {
  width: 100%;
  text-align: center;
  margin: 30px 0;
}

.teaser__pag-dot {
  text-indent: -9999px;
  border: 0;
  border-radius: 50%;
  width: 17px;
  height: 17px;
  padding: 0;
  margin: 5px 6px;
  background-color: #ccc;
  -webkit-appearance: none;
  cursor: pointer;

  &--current {
    background-color: #000;
  }
}
</style>
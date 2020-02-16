<template>
  <div id="app">
    <Loader :loaded="this.loaded" />
    <Nav :smoothScroller="smoothScroller"
         :clickAnchor="clickAnchor"
         :switchNav="switchNav"
         :navExpand="this.navExpand"
         :scrolled="this.scrolled"/>
    <Hero :smoothScroller="smoothScroller"
          :clickAnchor="clickAnchor"/>
    <div class="divider-bar gradient"></div>
    <About />
    <div class="divider-bar gradient flipped"></div>
    <Portfolio />
    <div class="divider-bar gradient"></div>
    <Skills />
    <div class="divider-bar gradient flipped"></div>
    <GMap />
    <Contact />

    <footer>
      <p>last updated feb 2020</p>
    </footer>
  </div>
</template>

<script>
import Nav from './components/Nav.vue'
import Loader from './components/Loader.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Portfolio from './components/Portfolio.vue'
import Skills from './components/Skills.vue'
import GMap from './components/GMap.vue'
import Contact from './components/Contact.vue'

export default {
  name: 'app',
  components: {
    Nav,
    Loader,
    Hero,
    About,
    Portfolio,
    Skills,
    GMap,
    Contact
  },
  methods: {
    handleScroll() {
      this.scrolled = window.scrollY > 120
    },
    switchNav() {
      this.navExpand = !this.navExpand
    },
    clickAnchor(e) {
      const id = e.target.hash.split('#')[1]
      const target = document.getElementById(id)
      if (this.navExpand) this.switchNav()
      const distance = Math.abs(target.getBoundingClientRect().top)
      if (distance < 30) return
      const duration = Math.floor(Math.abs(distance / 3))
      if (window.innerWidth < 768) {
        this.smoothScroller(target, duration, 0)
      }
      else {
        this.smoothScroller(target, duration, 60)
      }
    },
    smoothScroller(target, duration, offset) {
      const startPos = window.pageYOffset
      const distance = target.getBoundingClientRect().top - offset
      let startTime = null

      function animation(currentTime) {
        if (startTime === null) {
          startTime = currentTime
        }
        let timeElapsed = currentTime - startTime
        let run = ease(timeElapsed, startPos, distance, duration) // get next scrollTo Y coordinate
        window.scrollTo(0, run)
        if (timeElapsed < duration) {
          requestAnimationFrame(animation) // continue repeating this function
        }
      }

      function ease(t,b,c,d) {
        t /= d / 2
        if (t < 1) {
          return c / 2 * t * t + b
        }
        t--
        return -c / 2 * (t * (t - 2) - 1) + b
      }

      requestAnimationFrame(animation)
    }
  },
  created () {
    window.addEventListener('scroll', this.handleScroll);
  },
  destroyed () {
    window.removeEventListener('scroll', this.handleScroll);
  },
  data: () => ({
    loaded: false,
    navExpand: false,
    scrolled: false
  }),
  mounted() {
    this.loaded = true
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}
body, html {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  font-size: 14px;
}
section {
  position: relative;
  padding: 0;
  z-index: 0;
}
li, ul {
  list-style: none;
}
a {
  text-decoration: none;
  &:visited, &:active, &:focus {
    text-decoration: none;
    color: inherit;
    outline: none;
  }
}
img, a {
  display: block;
  height: auto;
  max-width: 100%;
}
img {
  pointer-events: none;
}
h1, h2, h4, p {
  // display: inline-block;
}
h1 {
  font-size: 3rem;
  margin: 2rem 0;
}
h2 {
  font-size: 2rem;
  margin: 15px auto;
}
h4 {
  margin: 10px 0;
}
p {
  font-size: 1.3rem;
  line-height: 1.63;
  margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  // color: #2c3e50;
  color: #2d2d2d;
}
.container {
  width: 90%;
  max-width: 1400px;
  margin: 0 auto;
  &.flex {
    display: flex;
  }
}
// $grad1: #b20744;
$grad1: #75aff1;
$grad2: #f8f9e3;
$grad3: #1d943e;
$grad4: #0f5a32;
$grad5: #1f1f1f;
.divider-bar {
  &.gradient {
    position: relative;
    z-index: 20;
    height: 11px;
    width: 100%;
    color: black;
    border-top: 1px solid;
    border-bottom: 1px solid;
    background: linear-gradient(45deg, $grad1 20%, $grad2 20%, $grad2 40%,
                                $grad3 40%, $grad3 60%, $grad4 60%, $grad4 80%,
                                $grad5 80%, $grad5 100%);
    &.flipped {
      transform: rotate(180deg);
    }
  }
}

footer {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100px;
  p {
    font-size: 14px;
    color: white;
    z-index: 0;
  }
}
</style>

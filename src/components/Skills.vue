<template lang="html">
  <section id="skills">
    <div class="container">
      <h2>~ skills ~</h2>
      <p>here's a sampling of the languages and tools i've implemented <nobr>in recent projects.</nobr></p>
    </div>

    <div class="skills-wrap">
      <div v-for="skill in skills" v-bind:key="skill" class="skill" @mouseenter="e => cardFlip(e)">
        <div class="skill-front">
          <p>{{ skill }}</p>
          <img :src="getImgUrl(skill)" alt=""/>
        </div>
        <div class="skill-back" :style="getRandomColor()">

        </div>
      </div>
    </div>

    <div class="container">
      <p>my list is always growing and shifting with the tides and trends of modern <nobr>software development.</nobr></p>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Skills',
  props: [],
  methods: {
    getImgUrl(image) {
      return require('../assets/icon-'+image+'.png')
    },
    cardFlip(e) {
      const card = e.target
      const random = Math.floor(Math.random() * Math.floor(3));
      let flipStyle
      if (random === 0) {
        flipStyle = 'tumble'
      }
      else if (random === 1) {
        flipStyle = 'flip'
      }
      else if (random === 2) {
        flipStyle = 'spin'
      }
      card.classList.add(flipStyle)
      setTimeout(() => {
        card.classList.remove(flipStyle)
      }, 2000)
    },
    getRandomColor() {
      return 'background-color: #'+Math.floor(Math.random()*16777215).toString(16);
    }
  },
  data: () => ({
    skills: [
      'html', 'javascript', 'css',
      'node', 'jquery', 'typescript',
      'react', 'redux', 'vue',
      'angular', 'ruby', 'python',
      'rails', 'aws', 'sql',
      'git', 'rspec', 'webpack',
    ]
  })
}
</script>

<style lang="scss" scoped>
  section {
    padding: 30px 0;
    background-color: rgba(31, 31, 31, .7);
    .container {
      h2 {
        // color: #f8f9e3;
        color: white;
        // color: #2c3e50;
      }
      p {
        color: white;
        margin: 0 0 15px;
      }
    }
    .skills-wrap {
      width: 94%;
      max-width: 450px;
      display: grid;
      grid-template-rows: 1fr;
      grid-template-columns: 1fr 1fr 1fr;
      margin: 0 auto 15px;
      .skill {
        position: relative;
        padding: 15px 10px;
        margin: 3px;
        min-height: 100px;
        transform-style: preserve-3d;
        &.tumble {
          animation: 1s linear tumble;
          pointer-events: none;
        }
        &.flip {
          animation: 1s linear flip;
          pointer-events: none;
        }
        &.spin {
          animation: 1s linear spin;
          pointer-events: none;
        }
        p {
          margin: 0 auto 5px;
          font-size: 1rem;
        }
        img {
          width: 50px;
          height: 50px;
          margin: 0 auto;
        }
        .skill-front, .skill-back {
          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;
          position: absolute;
          top: 0;
          left: 0;
          height: 100%;
          width: 100%;
          backface-visibility: hidden;
          border-radius: 10px;
          border: 1px solid;
          background-color: white;
        }
        .skill-back {
          transform: rotateY(180deg);
        }
      }
    }
  }

  @keyframes tumble {
    0% {
      transform: rotateX(0deg);
    }
    100% {
      transform: rotateX(360deg);
    }
  }

  @keyframes flip {
    0% {
      transform: rotateY(0deg);
    }
    100% {
      transform: rotateY(360deg);
    }
  }

  @keyframes spin {
    0% {
      transform: rotateZ(0deg);
    }
    100% {
      transform: rotateZ(360deg);
    }
  }

  @media screen and (min-width: 1024px) {
    section {
      .skills-wrap {
        max-width: 1024px;
        grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr;
      }
    }
  }
</style>

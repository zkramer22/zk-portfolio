<template lang="html">
  <section id="top">
    <img class="background parallax" src="../assets/keyboard.jpg" alt="">
    <div class="container">
      <h1>
        hey there!
        <br>
        i'm zach kramer.
      </h1>

      <div class="typer-wrap">
        <span id="typer-obj"></span><span :class="this.caret ? 'caret' : 'caret hidden'">|</span>
      </div>

      <a class="button" :href="publicPath" target="_blank">
        download resume
      </a>
      <a @click="(e) => this.clickAnchor(e)" class="button" href="#portfolio">
        view portfolio
      </a>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Hero',
  props: {
    smoothScroller: { type: Function },
    clickAnchor: { type: Function }
  },
  methods: {
    typeMessage(message) {
      return new Promise((resolve, reject) => {
        const letters = message.split('')
        let i = 0
        const len = letters.length
        const typerObj = document.getElementById('typer-obj')
        const typerInt = setInterval(() => {
          typerObj.innerHTML += `<span>${letters[i]}</span>`
          i++
          if (i === len) {
            clearInterval(typerInt)
            resolve(true)
            reject(false)
          }
        }, 55)
      })
    },
    switchCaret(inf) {
      return new Promise((resolve, reject) => {
        let i = 0
        const switchInt = setInterval(() => {
          this.caret = !this.caret
          i++
          if (!inf && i > 5) {
            clearInterval(switchInt)
            resolve(true)
            reject(false)
          }
        }, 420)
      })
    },
    deleteMessage() {
      return new Promise((resolve, reject) => {
        const typerObj = document.getElementById('typer-obj')
        let i = typerObj.children.length - 1
        const deleteInt = setInterval(() => {
          typerObj.lastChild.remove()
          i--
          if (i < 0) {
            clearInterval(deleteInt)
            resolve(true)
            reject(false)
          }
        }, 30)
      })
    },
    typingSequence(messages, i) {
      if (i === messages.length - 1) {
        this.typeMessage(messages[i]).then(() => {
          this.switchCaret(false)
        })
        return
      }
      else {
        this.typeMessage(messages[i]).then(() => {
          this.switchCaret().then(() => {
            this.deleteMessage().then(() => {
              this.typingSequence(messages, i + 1)
            })
          })
        })
      }
    }
  },
  data: () => ({
    caret: true,
    messages: [
      "i'm a software developer & designer.",
      "i love buiding & breaking things.",
      "let's work together to make something incredible!"
    ],
     publicPath: process.env.BASE_URL + 'zachkramer-resume.pdf'
  }),
  mounted() {
    setTimeout(() => {
      this.typingSequence(this.messages, 0)
    }, 2000)
  }
}
</script>

<style lang="scss" scoped>
  section {
    height: 100vh;
    border-bottom: 6px solid black;
    min-height: 600px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    // padding: 16vh 0 0;
    &::after {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      height: 110%;
      content: "";
      z-index: 1;
      background-color: rgba(0,0,0,0.69);
      pointer-events: none;
      min-height: 600px;
    }
    img.background {
      height: 100%;
      width: auto;
      max-width: unset;
      min-width: 100%;
    }
    a {
      color: white;
    }
    .parallax {
      position: fixed;
      top: 0;
    }
    .container {
      z-index: 10;
      color: white;
      .typer-wrap {
        margin: 0 auto;
        height: 115px;
        text-align: center;
        width: 90%;
        span {
          font-size: 1.55rem;
          font-weight: 400;
          opacity: 1;
          &.hidden {
            opacity: 0;
          }
        }
      }
      .button {
        margin: 0 auto 20px;
        width: 240px;
        border-radius: 100px;
        border: 2px solid;
        padding: 20px 10px;
        font-size: 1.5rem;
        font-weight: 900;
        background-color: rgba(0, 0, 0, 0.65);
        transition: background-color .1s linear;
        &:hover {
          background-color: #1d943e;
        }
      }
    }
  }

  @media screen and (min-width: 768px) {
    section {
      .container {
        .button {
          display: inline-block;
          margin: 10px;
        }
        .typer-wrap {
          span {
            font-size: 1.75rem;
          }
        }
      }
    }
  }
</style>

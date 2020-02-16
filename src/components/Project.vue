<template lang="html">
  <div class="project" @mouseover="hover = true" @mouseleave="hover = false" @mouseup="() => stopScroll()">
    <div class="container">
      <h4>
        {{ project.name }}
      </h4>
      <p>
        {{ project.description }}
      </p>
    </div>
    <div :class="project.arrows && this.hover ? 'scroll-arrow left active' : 'scroll-arrow left'"
      @mousedown="(e) => startScroll(e, false)">
      <img src="../assets/icon-arrow-right.png" alt="">
    </div>
    <div :class="project.arrows && this.hover ? 'scroll-arrow right active' : 'scroll-arrow right'"
      @mousedown="(e) => startScroll(e, true)">
      <img src="../assets/icon-arrow-right.png" alt="">
    </div>

    <div class="project-wrap">
      <div v-for="image in project.images" v-bind:key="image.id" class="project-screenshot">
        <img :src="getImgUrl(image.name)" alt=""/>
      </div>
    </div>

    <div class="project-links">
      <div v-show="project.github" class="link-wrap">
        <a class="button" :href="project.github" target="_blank">github</a>
      </div>
      <div class="link-wrap">
        <a class="button" :href="project.liveSite" target="_blank">live site</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Project",
  methods: {
    getImgUrl(image) {
      if (!image) {
        return
      }
      return require('../assets/'+image)
    },
    startScroll(e, right) {
      clearInterval(this.scrollInt)
      if (right) {
        const project = e.target.nextElementSibling
        let leftPos = project.scrollLeft
        this.scrollInt = null
        this.scrollInt = setInterval(() => {
          project.scrollTo(leftPos + 10, 0)
          leftPos = project.scrollLeft
        }, 0)
      }
      else {
        const project = e.target.nextElementSibling.nextElementSibling
        let leftPos = project.scrollLeft
        this.scrollInt = null
        this.scrollInt = setInterval(() => {
          project.scrollTo(leftPos - 10, 0)
          leftPos = project.scrollLeft
        }, 0)
      }
    },
    stopScroll() {
      clearInterval(this.scrollInt)
    }
  },
  props: {
    project: { type: Object },
    gifIndex: { type: Number }
  },
  data: () => ({
    hover: false,
    scrollInt: null,
    gif: false
  })
}
</script>

<style lang="scss">
  $grad2: #f8f9e3;
  #projects {
    display: block;
    width: 100%;
    .container {
      margin-bottom: 10px;
      h4 {
        font-size: 1.2rem;
        font-weight: 700;
      }
      p {
        font-size: 1rem;
        font-weight: 700;
        &:last-of-type {
          font-weight: normal;
        }
      }
    }
    .project {
      position: relative;
      padding-bottom: 40px;
      .scroll-arrow {
        position: absolute;
        width: 40px;
        top: 50%;
        border-radius: 50%;
        filter: invert(1);
        cursor: pointer;
        z-index: 2;
        opacity: 0;
        background-color: rgba(0,0,0,0);
        transition: opacity .2s linear, right .2s ease, left .2s ease, background-color .2s linear, filter .2s linear;
        &.left {
          left: 30px;
          &.active {
            opacity: 1;
            left: 10px;
          }
          img {
            transform: rotate(180deg)
          }
        }
        &.right {
          right: 30px;
          &.active {
            opacity: 1;
            right: 10px;
          }
        }
        img {
          width: 40px;
          margin: 0 auto;
        }
        &:hover {
          background-color: rgba(29,148,62,1);
          filter: invert(1) hue-rotate(180deg);
        }
      }
    }
    .project-wrap {
      display: flex;
      align-items: center;
      width: 100%;
      overflow-x: scroll;
      .project-screenshot {
        position: relative;
        min-width: 100vw;
        border-right: 5px solid #d8d8d8;
        box-sizing: content-box;
        img {
          display: block;
          width: 100%;
          height: auto;
          &.hidden {
            display: none;
          }
        }
        &:last-of-type {
          border-right: none !important;
        }
      }
      div:last-of-type {
        border-right: none;
      }
    }
    .project-links {
      display: flex;
      justify-content: center;
      .link-wrap {
        width: 100%;
        border-top: 2px solid black;
        border-right: 2px solid black;
        background-color: rgb(255, 255, 255);
        box-shadow: 0px 4px 2px -1px grey;
        position: relative;
        transition: all .09s linear;
        &:active {
          box-shadow: 0px 0px 0px 0px grey;
        }
        a {
          display: block;
          padding: 15px 0;
          font-size: 1.4rem;
          color: #2c3e50;
          text-decoration: none;
          outline: none;
          &:active, &:focus {
            outline: none;
          }
        }
        &:nth-of-type(2) {
          border-right: none;
        }
      }
    }
    div:last-of-type {
      padding-bottom: 0;
    }
  }

  @media screen and (min-width: 1024px) {
    #projects {
      display: flex;
      flex-wrap: wrap;
      .project {
        width: 50%;
        // margin-bottom: 0;
        // padding-bottom: 40px;
        .container {
          min-height: 77px;
        }
        .scroll-arrow {
          top: 50%;
        }
        &:nth-child(odd) {
          border-right: 5px solid black;
        }
      }
      .project-wrap {
        .project-screenshot {
          min-width: 50vw;
        }
      }
      .project-links {
        border-bottom: 5px solid black;
      }
      div:nth-of-type(7), div:nth-of-type(8) {
        .project-links {
          border-bottom: none;
        }
      }
      div:nth-of-type(1).project, div:nth-of-type(2).project {
        border-top: 5px solid black;
      }
    }
  }
</style>

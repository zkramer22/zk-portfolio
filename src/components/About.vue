<template lang="html">
  <section id="about">
    <div id="headshot-wrap">
      <img src="../assets/headshot-3.jpg" alt="zach kramer">
      <!-- <img class="desktop-only" src="../assets/headshot-2.jpg" alt=""> -->
      <img class="desktop-only" src="../assets/z-no-t.jpg" alt="">
    </div>
    <div class="container">
      <h2>~ about ~</h2>
      <p>
          I'm a 26-year old software developer from Philadelphia
          with a creative mind and a passion for technology.

          After attending college and working as a freelance musician
          and producer for a few years, my fascination with software
          development became more and more apparent. I got my footing
          by developing business solutions with FileMaker Pro for a small
          software company called The Tricon Group in Garnett Valley, PA.

          In January of 2018 I made my move to NYC and attended
          <a href="http://appacademy.io" target="_blank">App Academy</a>, one
          of the nation's top software development bootcamps.

          Fast forward to 2020: I've worked as a frontend developer for <a href="https://onemagnify.com" target="_blank">OneMagnify</a>
          and <a href="https://gsw-w.com" target="_blank"><nobr>GSW Worldwide</nobr></a>,
          where I've fine tuned my skills with design, development, animation,
          and more – all while collaborating with expert level UX designers,
          account managers, and other dev teams.
          With my creativity and abundance of skills &amp; knowledge all around
          the stack, I am confident that I can be a valuable asset to any development team
          building tomorrow's web technologies from the ground up.
      </p>
    </div>
  </section>
</template>

<script>
export default {
  name: 'About',
  props: [],
  methods: {
  }
}
</script>

<style lang="scss" scoped>
  section {
    z-index: 3;
    background-color: #1f1f1f;
    // padding: 0 0 15px;
    padding: 0 0 30px 0;
    #headshot-wrap {
      position: relative;
      top: 0;
      left: 0;
      width: 100vw;
      height: auto;
      img {
        max-width: 100%;
      }
      .desktop-only {
        display: none;
      }
      &:after {
        position: absolute;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
        content: "";
        background: linear-gradient(rgba(0, 0, 0, 0) 70%, #1f1f1f 100%);
      }
    }
    .container {
      p {
        text-align: justify;
        color: white;
        a {
          display: inline;
          color: lightgreen;
          &:active, &:visited {
            color: lightgreen;
          }
        }
      }
    }
  }
  h2 {
    color: white;
    margin-top: 30px;
  }
  @media screen and (min-width: 768px) {
    section {
      #headshot-wrap {
        display: flex;
        img {
          max-width: 50%;
        }
        .desktop-only {
          display: block;
        }
      }
    }
  }
</style>

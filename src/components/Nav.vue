<template>
  <nav :class="this.scrolled ? 'nav sticky': 'nav'">
    <div class="container flex">
      <div class="logo-wrap">
        <a @click="(e) => this.clickAnchor(e)" class="smooth-scroll" href="#top">
          <img class="smooth-scroll" src="../assets/icon-z-key.png"/>
        </a>
      </div>

      <div class="nav-menu-wrap">
        <div id="hamburger" @click="this.switchNav">
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </div>

        <div :class="this.navExpand ? 'nav-menu-mobile expanded' : 'nav-menu-mobile'">
          <div class="container">
            <div id="close-menu" @click="this.switchNav">
              <span class="x1"></span>
              <span class="x2"></span>
            </div>
            <div class="nav-links-wrap">
              <a @click="(e) => this.clickAnchor(e)" class="nav-menu-item smooth-scroll" href="#about">about</a>
              <a @click="(e) => this.clickAnchor(e)" class="smooth-scroll" href="#portfolio">portfolio</a>
              <a @click="(e) => this.clickAnchor(e)" class="smooth-scroll" href="#skills">skills</a>
              <a @click="(e) => this.clickAnchor(e)" class="smooth-scroll" href="#contact">contact</a>
            </div>
          </div>
        </div>

        <div class="nav-menu">
          <div class="nav-links-wrap">
            <a @click="(e) => this.clickAnchor(e)" class="nav-menu-item smooth-scroll" href="#about">about</a>
            <a @click="(e) => this.clickAnchor(e)" class="smooth-scroll" href="#portfolio">portfolio</a>
            <a @click="(e) => this.clickAnchor(e)" class="smooth-scroll" href="#skills">skills</a>
            <a @click="(e) => this.clickAnchor(e)" class="smooth-scroll" href="#contact">contact</a>
          </div>
        </div>
      </div>
    </div>

  </nav>

</template>

<script>
export default {
  name: 'Nav',
  props: {
    smoothScroller: { type: Function },
    clickAnchor: { type: Function },
    switchNav: { type: Function },
    navExpand: { type: Boolean },
    scrolled: { type: Boolean }
  },
  data: () => ({})
}
</script>

<style lang="scss" scoped>
  nav {
    position: fixed;
    z-index: 50;
    top: 0;
    left: 0;
    right: 0;
    height: 85px;
    padding: 15px 0;
    transition: all .2s linear;
    .container {
      justify-content: space-between;
      .logo-wrap {
        a, img {
          width: 55px;
          transition: all .2s linear;
        }
        a img {
          background-color: white;
          border-radius: 10%;
        }
      }
      .nav-menu-wrap {
        #hamburger {
          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;
          width: 55px;
          height: 55px;
          span {
            width: 35px;
            margin: 2px auto;
            background-color: white;
            height: 5px;
            border: 1px solid black;
            border-radius: 7px;
          }
        }
        .nav-menu {
          display: none;
        }
        .nav-menu-mobile {
          display: block;
          position: fixed;
          // bottom: 0;
          // left: 100vw;
          // transition: left .4s ease;
          left: 0;
          top: -55vh;
          opacity: 0;
          transition: top .4s ease, opacity .4s linear;
          width: 100vw;
          background-color: rgba(0,0,0,.93);
          padding: 15px 0;
          border-bottom: 5px solid white;
          a {
            color: white;
            display: block;
            max-width: 150px;
            height: 70px;
            line-height: 70px;
            margin: 0 auto;
            font-size: 2rem;
          }
          &.expanded {
            // left: 0;
            top: 0;
            opacity: 1;
          }
          .container {
            position: relative;
            #close-menu {
              position: absolute;
              right: 0;
              top: 0;
              width: 55px;
              height: 55px;
              span {
                display: block;
                position: absolute;
                width: 35px;
                height: 5px;
                background-color: white;
                border: 1px solid black;
                border-radius: 7px;
              }
              .x1 {
                transform: rotate(45deg) translate(25px, 10px);
              }
              .x2 {
                transform: rotate(-45deg) translate(-10px, 25px);
              }
            }
          }
        }
      }
    }
  }

  @media screen and (min-width: 768px) {
    nav {
      .container {
        .nav-menu-wrap {
          display: flex;
          align-items: center;
          #hamburger {
            display: none;
          }
          .nav-menu-mobile {
            display: none;
          }
          .nav-menu {
            display: block;
            background-color: rgba(0,0,0,0);
            width: auto;
            .nav-links-wrap {
              display: flex;
              justify-content: space-around;
              a {
                color: white;
                margin: 0 15px;
                padding: 0 15px;
                font-size: 1.1em;
                transition: color .1s linear;
                font-weight: 700;
                height: 40px;
                line-height: 40px;
                &:hover {
                  color: lightgreen;
                }
              }
            }
          }
        }
      }
      &.sticky {
        background-color: black;
        height: 60px;
        padding: 5px;
        .container {
          height: 100%;
          .logo-wrap {
            display: flex;
            align-items: center;
            a, img {
              width: 40px;
            }
          }
        }
      }
    }
  }
</style>

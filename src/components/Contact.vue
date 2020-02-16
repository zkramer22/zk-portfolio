<template lang="html">
  <section id="contact">
    <h2>~ contact ~</h2>
    <p>let's talk tech and see how we can bring your project to life!</p>
    <p>feel free to call / text, email, or message me on LinkedIn.</p>
    <br>
    <!-- <form class="" action="index.html" method="post">

    </form> -->
    <div class="container">
      <div class="contact-icons-wrap">
        <div class="contact-icon">
          <a href="tel:2677603054" target="_blank">
            <img src="../assets/icon-phone.png" alt="">
            <span>267.760.3054</span>
          </a>
        </div>
        <div class="contact-icon">
          <a href="mailto:zkramer22@gmail.com" target="_blank">
            <img src="../assets/icon-mail.png" alt="">
            <span>zkramer22@gmail.com</span>
          </a>
        </div>
        <div class="contact-icon">
          <a href="https://linkedin.com/in/zkramer22" target="_blank">
            <img src="../assets/icon-linkedin.png" alt="">
            <span>linkedin: zkramer22</span>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Contact",
  props: [],
  data: () => ({
    socials: false
  })
}
</script>

<style lang="scss" scoped>
  $grad2: #f8f9e3;
  section {
    background-color: $grad2;
    padding: 30px 0;
    .container {
      .contact-icons-wrap {
        display: flex;
        flex-direction: column;
        width: 100%;
        align-items: center;
        .contact-icon {
          margin: 20px;
          height: auto;
          a {
            display: block;
            color: #2d2d2d;
            font-size: 15px;
            width: fit-content;
            margin: 0 auto;
            img {
              width: 80px;
              margin: 0 auto;
              border-radius: 50%;
              border: 4px solid white;
              box-shadow: 0px 4px 6px 0px #949494;
            }
            span {
              display: block;
              margin-top: 15px;
            }
          }
        }
      }
    }
  }

  @media screen and (min-width: 768px) {
    section {
      .container {
        .contact-icons-wrap {
          flex-direction: row;
          justify-content: center;
          .contact-icon {
            width: 33%;
          }
        }
      }
    }
  }
</style>

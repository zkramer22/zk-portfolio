<template lang="html">
  <div id="preloader" :class="loaded ? 'loaded' : ''">
    <img src="../assets/icon-z-key.png" alt="">
    <div class="loader">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Loader',
  props: ['loaded']
}
</script>

<style lang="scss" scoped>
  #preloader {
    position: fixed;
    display: flex;
    justify-content: center;
    align-items: center;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    background: #ffffff;
    z-index: 999;
    -webkit-transition: all .5s ease;
    -moz-transition: all .5s ease;
    transition: all .5s ease;
    pointer-events: none;
    &.loaded {
      opacity: 0;
      visibility: hidden;
    }
    img {
      position: absolute;
      width: 50px;
      height: 50px;
      z-index: 1000;
      transform: scale(100%);
      animation: pulse 2s ease infinite;
    }
  }

  .loader {
    display: block;
    position: relative;
    width: 150px;
    height: 150px;
    border-radius: 50%;
    border: 3px solid transparent;
    border-top-color: #24b662;
    -webkit-animation: spin 2s linear infinite;
    animation: spin 2s linear infinite;
    &:before {
      content: "";
      position: absolute;
      top: 5px;
      left: 5px;
      right: 5px;
      bottom: 5px;
      border-radius: 50%;
      border: 3px solid transparent;
      border-top-color: #24b662;
      -webkit-animation: spin 3s linear infinite;
      animation: spin 3s linear infinite;
    }
    &:after {
      content: "";
      position: absolute;
      top: 15px;
      left: 15px;
      right: 15px;
      bottom: 15px;
      border-radius: 50%;
      border: 3px solid transparent;
      border-top-color: #24b662;
      -webkit-animation: spin 1.5s linear infinite;
      animation: spin 1.5s linear infinite;
    }
  }

  @-webkit-keyframes spin {
    0%   {
        -webkit-transform: rotate(0deg);
        -ms-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(360deg);
        -ms-transform: rotate(360deg);
        transform: rotate(360deg);
    }
  }

  @-webkit-keyframes pulse {
    0% {
      -webkit-transform: scale(1);
      -ms-transform: scale(1);
      transform: scale(1);
    }
    50% {
      -webkit-transform: scale(1.3);
      -ms-transform: scale(1.3);
      transform: scale(1.3);
    }
    100% {
      -webkit-transform: scale(1);
      -ms-transform: scale(1);
      transform: scale(1);
    }
  }

  @keyframes spin {
    0%   {
        -webkit-transform: rotate(0deg);
        -ms-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(360deg);
        -ms-transform: rotate(360deg);
        transform: rotate(360deg);
    }
  }

  @keyframes pulse {
    0% {
      -webkit-transform: scale(1);
      -ms-transform: scale(1);
      transform: scale(1);
    }
    50% {
      -webkit-transform: scale(1.3);
      -ms-transform: scale(1.3);
      transform: scale(1.3);
    }
    100% {
      -webkit-transform: scale(1);
      -ms-transform: scale(1);
      transform: scale(1);
    }
  }
</style>

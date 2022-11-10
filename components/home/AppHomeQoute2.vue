<template>
    <section class="banner2 ">
      <div class="overlay"></div>
      <svg class="top_seperator" xmlns="http://www.w3.org/2000/svg" version="1.1" fill="#fff" width="100%" height="100" viewBox="0 0 4 0.266661" preserveAspectRatio="none" style="height: 100px;"><polygon class="fil0" points="4,0 4,0.266661 -0,0.266661 "></polygon></svg>
      <div class="row m-0 content justify-content-center">
          <h3>Our reputation is the proof!</h3>
          <h4>– The7 Modern Business –</h4>
      </div>
      <svg class="bootom_seperator" xmlns="http://www.w3.org/2000/svg" version="1.1" fill="#fff" width="100%" height="100" viewBox="0 0 4 0.266661" preserveAspectRatio="none" style="height: 100px;"><polygon class="fil0" points="4,0 4,0.266661 -0,0.266661 "></polygon></svg>
  </section>
</template>

<script>

export default {
    name: 'AppHomeQoute',
    data() {
        return {
            
        }
    },
    methods : {
        
    }
}
</script>

<style>
    .banner2 {
      background-color: rgba(0, 0, 0, 0);
      background-image: url("https://the7.io/modern-business/wp-content/uploads/sites/53/2018/12/t-img047.jpg");
      background-repeat: no-repeat;
      background-size: cover;
      background-attachment: fixed;
      position: relative;
      z-index: 0;
    }
    .banner2 .content {
      padding-bottom: 40px;
      padding-left: 25px;
      padding-right: 25px;
      padding-top: 40px;
      z-index: 1;
      position: relative;
    }
    .banner2 .content h3 {
      font-size: 34px;
      font-weight: 700;
      line-height: 44px;
      margin-bottom: 15px;
      color: #fff;
      text-align: center;
    }
    .banner2 .content h4 {
      color: var(--main-color);
      display: inline-block;
      font-size: 24px;
      font-weight: 700;
      line-height: 34px;
      text-align: center;
    }
    .top_seperator {
      bottom: auto;
      -webkit-transform: scale(-1);
      -ms-transform: scale(-1);
      transform: scale(-1);
      position: relative;
      z-index: 1;
    }
    .bootom_seperator {
      position: relative;
      z-index: 1;
    }
    .banner2 .overlay {
        position: absolute;
        width: 100%;
        height: 100% !important;
        left: 0;
        top: 0;
        background-color: rgba(38,45,55,0.5);
    }
</style>
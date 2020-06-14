<template>
  <main>
    <div class="best-lp">
      <div class="container">
        <div class="left-column">
          <div>
            <img src="../assets/images/app-icon.svg" alt="app-icon">
          </div>
          <div>
            <h1><strong>AppStarter.</strong> Best landing page for web and mobile apps</h1>
            <div class="btns-wrap">
              <a href="javascript:void(0);" class="download">Download Now</a>
              <a href="javascript:void(0);" class="watch">Watch Video</a>
            </div>
          </div>
        </div>
        <div class="right-column">
          <img src="../assets/images/tablet-img.png"
               srcset="../assets/images/tablet-img@2x.png 2x, ../assets/images/tablet-img@3x.png 3x"
               alt="app-icon">
        </div>
      </div>
    </div>
    <div class="why-we-use">
      <div class="container">
        <div class="why-we-use-content">
          <h2><strong>Why</strong>   do we use it?</h2>
          <p>
            This sounded nonsense to Alice, so she said nothing, but set off at once toward the
            Red Queen. To her surprise, she lost sight of her in a moment.
          </p>
          <Timers />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import Timers from './Timers.vue';

export default {
  name: 'Main',
  components: {
    Timers,
  },
};
</script>

<style scoped lang="scss">
  main {
    flex: 1 0 auto;
  }
  .best-lp {
    max-height: 720px;
    padding-top: 137px;
    background: #5A81F0 url('../assets/images/header-bg.jpg') no-repeat;
    .container {
      display: flex;
      justify-content: space-between;
    }
    .left-column {
      padding-top: 93px;
    }
    .right-column {
      padding-right: 44px;
    }
    h1 {
      color: #fff;
      max-width: 530px;
      font-weight: 300;
      font-size: 35px;
      line-height: 50px;
      letter-spacing: 0.7px;
      margin: 12px 0 36px;
      strong {
        font-weight: 800;
        letter-spacing: 1px;
      }
    }
    .btns-wrap {
      display: flex;
      align-items: center;
      a {
        font-weight: bold;
        font-size: 17px;
        line-height: 23px;
        text-align: center;
        letter-spacing: 1px;
        padding: 14px 16px 13px;
        border-radius: 6px;
        text-decoration: none;
        box-shadow: 0 6px 12px rgba(40, 43, 49, 0.08);
      }
    }
    .download {
      color: #fff;
      margin-right: 20px;
      background: linear-gradient(163.33deg, #FF8E64 0%, #FFE641 100%);
    }
    .watch {
      color: #282B31;
      background: #fff;
    }
  }
  .why-we-use {
    padding: 220px 0 112px;
    background: #F2F2F2;
    &-content {
      width: 770px;
      margin: 0 auto;
    }

    h2 {
      font-weight: 300;
      font-size: 35px;
      line-height: 50px;
      text-align: center;
      letter-spacing: 1px;
      color: #282B31;
      margin-bottom: 0;
      strong {
        font-weight: 800;
      }
    }
    p {
      max-width: 590px;
      font-size: 16px;
      line-height: 30px;
      text-align: center;
      color: #676C75;
      margin: 16px auto 60px;
    }
  }
</style>

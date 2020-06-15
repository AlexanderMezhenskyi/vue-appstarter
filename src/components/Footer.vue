<template>
  <footer>
    <div class="container">
      <div>
        <a href="#" class="brand-name">AppStarter</a>
      </div>
      <div class="creator">
        <div>
          Created with <i class="mdi mdi-heart"></i> by <b>Sergey Azovskiy</b>
        </div>
        <div>&copy; AppStarter, 2017</div>
      </div>
      <div class="social-icons">
        <a href="https://twitter.com/" target="_blank" class="twitter">
          <i class="mdi mdi-twitter"></i>
        </a>
        <a href="https://www.facebook.com/" target="_blank" class="facebook">
          <i class="mdi mdi-facebook"></i>
        </a>
        <a href="https://www.instagram.com/" target="_blank" class="instagram">
          <i class="mdi mdi-instagram"></i>
        </a>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
};
</script>

<style scoped lang="scss">
  footer {
    padding: 14px 0 32px;
    flex: 0 0 auto;
    @media screen and (max-width: 490px) {
      padding: 14px 0;
    }
  }
  .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    @media screen and (max-width: 490px) {
      flex-direction: column;
    }
  }
  .brand-name {
    font-weight: 800;
    font-size: 20px;
    line-height: 25px;
    color: #282B31;
    text-decoration: none;
  }
  .creator {
    font-size: 11px;
    line-height: 15px;
    color: #999EA8;
    text-align: center;
    padding-top: 20px;
    @media screen and (max-width: 490px) {
      padding-bottom: 20px;
    }
    i {
      color: #FF4876;
      font-size: 140%;
    }
    b {
      color: #282B31;
    }
    > div:last-child {
      margin-top: 12px;
    }
  }
  .social-icons {
    display: flex;
    align-items: center;
    border: 1px solid #E7E8EA;
    border-radius: 6px;
      a {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 40px;
        height: 40px;
        color: #B9BDC3;
        i {
          font-size: 130%;
        }
      }
      .facebook {
        border-left: 1px solid #E7E8EA;
        border-right: 1px solid #E7E8EA;
      }
  }
</style>

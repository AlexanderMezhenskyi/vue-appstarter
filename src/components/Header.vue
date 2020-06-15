<template>
  <header>
    <div class="container">
      <div>
        <a href="#" class="brand-name">AppStarter</a>
      </div>
      <nav ref="nav">
        <ul>
          <li><a href="#">Features</a></li>
          <li><a href="#">Video Tour</a></li>
          <li><a href="#">Reviews</a></li>
          <li><a href="#">Pricing</a></li>
        </ul>
        <button type="button" class="get-free">Get it free</button>
      </nav>
      <button type="button" class="mobile-menu" @click="toogleMenu">
        <i class="mdi mdi-menu"></i>
      </button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  methods: {
    toogleMenu() {
      this.$refs.nav.classList.toggle('active');
    },
  },
  mounted() {
    window.addEventListener('resize', () => {
      if (window.innerWidth > 767) {
        this.$refs.nav.classList.remove('active');
      }
    });
  },
};
</script>

<style scoped lang="scss">
  header {
    position: absolute;
    width: 100%;
    flex: 0 0 auto;
    color: #fff;
    padding-top: 18px;
  }
  .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  nav {
    display: flex;
    align-items: center;
    @media screen and (max-width: 767px) {
      display: none;
    }
    &.active {
      display: block;
      position: fixed;
      top: 50px;
      left: 0;
      width: 100%;
      background: #5A81F0;
      text-align: center;
      padding-bottom: 25px;
    }
  }
  a {
    color: #fff;
    text-decoration: none;
  }
  .brand-name {
    font-weight: 800;
    font-size: 20px;
    line-height: 27px;
  }
  ul {
    list-style-type: none;
    @media screen and (max-width: 767px) {
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 0;
    }
  }
  li {
    display: inline-block;
    padding: 0 16px;
    @media screen and (max-width: 767px) {
      padding: 5px 16px;
    }
    a {
      font-size: 15px;
      line-height: 20px;
    }
  }
  .get-free {
    color: #282B31;
    font-weight: bold;
    font-size: 14px;
    line-height: 19px;
    background: #FFFFFF;
    border-radius: 6px;
    padding: 10px 20px;
    margin-left: 14px;
    text-align: center;
    text-transform: uppercase;
    letter-spacing: 1px;
    @media screen and (max-width: 767px) {
      margin-left: 0;
    }
  }
  .mobile-menu {
    display: none;
    width: 30px;
    height: 30px;
    color: #fff;
    background: transparent;
    @media screen and (max-width: 767px) {
      display: block;
    }
    i {
      font-size: 150%;
    }
  }
</style>

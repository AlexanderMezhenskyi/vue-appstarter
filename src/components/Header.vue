<template>
  <header>
    <div class="container">
      <div>
        <a href="#" class="brand-name">AppStarter</a>
      </div>
      <nav>
        <ul>
          <li><a href="#">Features</a></li>
          <li><a href="#">Video Tour</a></li>
          <li><a href="#">Reviews</a></li>
          <li><a href="#">Pricing</a></li>
        </ul>
        <button type="button" class="get-free">Get it free</button>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
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
  }
  li {
    display: inline-block;
    padding: 0 16px;
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
  }
</style>

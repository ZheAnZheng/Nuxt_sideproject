<template>
  <nav>
    <ul>
      <li>
        <nuxt-link to="/carts">首頁</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/carts/new">新增</nuxt-link>
      </li>
    </ul>
  </nav>
</template>
<style lang="scss" scoped>
nav {
    padding-left:2rem;
  height: 75px;
  width: 100%;
  ul {
    
    width:25%;
    display: flex;
    flex-direction: row;
    padding: 15px;
    
    height: 100%;
    li {
      height: 100%;
      width:100%;
      text-align:center;
      line-height:45px;
    }
  }
  a{
    display:block;
    height: 100%;
    width: 100%;
    color:var(--primary-text-color);
    &.nuxt-link-active {
        color:var(--primary-color);
      border-bottom: 2px solid var(--primary-color);
    }
  }
}
</style>

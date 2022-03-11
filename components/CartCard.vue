<template>
  <li>
    <nuxt-link :to="{name:'carts-id' , params:{id:cart.id}}" class="context-container">
        <img :src="cart.image" />
        <div class="card-title">{{cart.brand}} {{cart.Version}}</div>
        <div>車齡{{cart.age}}年</div>
    </nuxt-link>
  </li>
</template>
<script>
export default {
  props: {
      cart:{
          type: Object,
          required: true,
      }
  },
};
</script>
<style lang="scss" scoped>
li {
  border-radius: 7px;
  box-shadow: 2px 2px 3px rgba(0, 0, 0, 0.2);
  width: 100%;
  height: 100%;
  color:var(--primary-text-color);
  background-color: var(--primary-bg-color);
}
.context-container{
    display:block;
    padding:1rem;
    color:var(--primary-text-color);
    .card-title{
        font-size:2.5rem;
    }
}
</style>

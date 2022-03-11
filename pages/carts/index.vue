<template>
  <div>
    <Navbar />
    <div class="cart-list-container">
      <ul class="cart-card-container">
        <CartCard  v-for="cart in carts" :key="cart.id" :cart="cart" />
      </ul>
    </div>
  </div>
</template>
<script>
export default {
    props:{
        carts:{
            type:Array,
            requred:true
        }
    }
  
};
</script>
<style lang="scss" scoped>
.cart-list-container {
  padding: 2rem;
}
.cart-card-container {
  grid-gap: 1rem;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

}
</style>

<template>
  <div class="container">
    <img :src="cart.image" />
    <div class="title"> {{cart.brand}} {{cart.Version}}</div>
    <div class="age">車齡 {{cart.age}}年</div>
    <div class="btn-wrapper">

      <baseButton @handleClick="goBack">返回首頁 </baseButton>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    carts: {
      type: Array,
      required: true,
    },
  },
  data(){
    return{
      cart:{}
    }
  },
  watch:{
    carts(){
      const {id }=this.$route.params;
      this.loadCartData(id);
    }
  },
  created(){
    const {id }=this.$route.params;
    this.loadCartData(id);
  },
  methods:{
    loadCartData(id){
      this.carts.forEach(cart => {
        console.log(cart.id==id)
       if(cart.id==id){
         this.cart={
           ...cart
         }
       }
      });
    },
    goBack(){
      this.$router.push('/carts');
    }
  }
};
</script>

<style lang="scss" scoped>
.container{
  padding:2rem;
  
  img{
    width:50%;
    min-width:300px;
    height:100%;
  }
  .title{
    font-size:3.5rem;
  }
  .age{
    font-size:2rem;
  }

}
.btn-wrapper{
  position:absolute;
  bottom:2rem;
  right:2rem;
  width:50px;
  height:50px;
}
</style>

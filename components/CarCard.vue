<template>
  <li>
    <nuxt-link :to="{name:'cars-id' , params:{id:car.id}}" class="context-container">
      <div class="img-wrapper"> 
        <img :src="car.image" />
      </div>
        <div class="card-title">{{car.brand}} {{car.Version}}</div>
        <div>車齡{{car.age}}年</div>
    </nuxt-link>
  </li>
</template>
<script>
export default {
  props: {
      car:{
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
.img-wrapper{
  width:100%;
  min-height:150px;
  height:100%;
  background-color:var(--mute-color);
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

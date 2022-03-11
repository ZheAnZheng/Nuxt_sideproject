<template>
  <div>
    <Navbar />
    <div class="car-list-container">
      <ul class="car-card-container">
        <CarCard  v-for="car in cars" :key="car.id" :car="car" />
      </ul>
    </div>
  </div>
</template>
<script>
export default {
    props:{
        cars:{
            type:Array,
            requred:true
        }
    }
    
};
</script>
<style lang="scss" scoped>
.car-list-container {
  padding: 2rem;
}
.car-card-container {
  grid-gap: 1rem;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

}
</style>

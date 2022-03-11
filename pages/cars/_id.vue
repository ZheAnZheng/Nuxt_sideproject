<template>
  <div class="container">
    <img :src="car.image" />
    <div class="title">{{ car.brand }} {{ car.Version }}</div>
    <div class="age">車齡 {{ car.age }}年</div>
    <div class="price">${{ car.price }}</div>
    <div class="description">{{ car.description }}</div>
    <div class="btn-wrapper">
      <baseButton @handleClick="backToCarIndex">返回首頁 </baseButton>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cars: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      car: {},
    };
  },
  watch: {
    cars() {
      const { id } = this.$route.params;
      this.loadcarData(id);
    },
  },
  created() {
    const { id } = this.$route.params;
    this.loadcarData(id);
  },
  methods: {
    loadcarData(id) {
      this.cars.forEach((car) => {
        console.log(car.id == id);
        if (car.id == id) {
          this.car = {
            ...car,
          };
        }
      });
    },
    backToCarIndex() {
      this.$router.push("/cars");
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  padding: 2rem;
  color: var(--primary-text-color);
  img {
    width: 50%;
    min-width: 300px;
    height: 100%;
  }
  .title {
    font-size: 3.5rem;
  }
  .age,
  .price {
    font-size: 2rem;
  }
  .description {
    font-size: 1.5rem;
  }
}
.btn-wrapper {
  position: sticky;
  bottom: 2rem;
  left: 95%;
  width: 50px;
  height: 50px;
}
</style>

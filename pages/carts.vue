<template>
    <nuxt-child :carts="carts"/>
</template>

<script>
export default {

  name: "IndexPage",
  created() {
    this.fetchCarts();
  },
  data() {
    return {
      carts: [],
    };
  },
  methods: {
    //   抓取mocki資料
    async fetchCarts() {
      try {
        const response = await fetch(
          "https://mocki.io/v1/907d6ac2-272f-40bb-98c3-785ff34f44c9"
        );
        const { cart } = await response.json();
        this.carts = [...cart];
      } catch (e) {
        console.log(e);
      }
    },
  },
  layout:'main',
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/color.scss";

</style>

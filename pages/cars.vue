<template>
  <nuxt-child :cars="cars" :formItems="formItems" @handleSubmit="addCar" />
</template>

<script>
export default {
  name: "IndexPage",
  created() {
    this.fetchCars();
  },
  data() {
    return {
      cars: [],
      // 用這樣的方式建立表單，只要接收emit就可以直接增加car，不需要從pages/cars/new傳遞資料回來
      formItems: [
        {
          id: 0,
          name: "照片",
          type: "file",
          value: "",
        },
        {
          id: 1,
          name: "品牌",
          type: "select",
          selectItems: [
            { id: 0, value: "TOYOTA" },
            { id: 1, value: "HONDA" },
            { id: 2, value: "BENZ" },
            { id: 3, value: "BMW" },
            { id: 4, value: "AUDI" },
            { id: 5, value: "NISSAN" },
            { id: 6, value: "LEXUS" },
            { id: 7, value: "SKODA" },
          ],
          value: "",
        },
        {
          id: 2,
          name: "型號",
          type: "select",
          selectItems: [
            { id: 0, value: "v1" },
            { id: 1, value: "v2" },
            { id: 2, value: "v3" },
            { id: 3, value: "v4" },
            { id: 4, value: "v5" },
            { id: 5, value: "v6" },
            { id: 6, value: "v7" },
            { id: 7, value: "v7" },
          ],
          value: "",
        },
        {
          id: 3,
          name: "車齡",
          type: "number",
          value: "",
        },
        {
          id: 4,
          name: "價格",
          type: "number",
          value: "",
        },
        {
          id: 5,
          name: "描述",
          type: "text",
          value: "",
        },
      ],
    };
  },
  methods: {
    //   抓取mocki資料
    async fetchCars() {
      try {
        const response = await fetch(
          "https://mocki.io/v1/bc8049cf-d6f0-4ffb-a855-1df9787a9faa"
        );
        const { cars } = await response.json();

        this.cars = [...cars];
      } catch (e) {
        console.log(e);
      }
    },
    addCar() {
      const newCar = {
        id: Math.random() * 1000,
        image: this.formItems[0].value,
        brand: this.formItems[1].value,
        version: this.formItems[2].value,
        age: this.formItems[3].value,
        price: this.formItems[4].value,
        description: this.formItems[5].value,
      };
      this.cars.push(newCar);
    },
  },
  layout: "main",
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/color.scss";
</style>

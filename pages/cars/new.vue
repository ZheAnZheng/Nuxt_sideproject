<template>
  <div class="container">
    <form @submit.prevent.stop="handleSubmit">
      <BaseInput v-for="item in formItems" :key="item.id" :inputData="item" />
      <BaseButton class="form-btn">提交</BaseButton>
    </form>
    <div class="btn-wrapper">
      <BaseButton @handleClick="backToCarIndex">返回首頁</BaseButton>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    formItems: {
      type: Array,
      required: true,
    },
  },
  computed: {
    items() {
      return this.formItems;
    },
  },
  methods:{
    backToCarIndex(){
      this.$router.push('/cars')
    },
    handleSubmit(){
      this.$emit('handleSubmit');
      this.backToCarIndex()
    }
  }
};
</script>
<style lang="scss" scoped>
.container {
  width: 100%;
  height: 100%;
}
form {
  margin-top: 5rem;
  margin-left: auto;
  margin-right: auto;
  padding: 2rem;
  height: 100%;
  width: 700px;
  min-width: 400px;
  background-color: var(--primary-bg-color);
  border-radius: 10px;
}
.form-btn {
  width: 100%;
  min-width: 250px;
  height: 50px;
  margin-top: 4rem;
}
.btn-wrapper {
  position: sticky;
  bottom: 5%;
  width: 50px;
  height: 50px;
  left: 92%;
}
</style>

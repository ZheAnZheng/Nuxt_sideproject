<template>
  <div class="container">
    
    <form @submit.prevent.stop="handleSubmit">
      <BaseInput v-for="item in modeFormItems" :key="item.id" :inputData="item" />
      <BaseButton class="form-btn">提交</BaseButton>
    </form>
    <div class="btn-wrapper">
      <BaseButton class="btn" @handleClick="toggleMode">輸入模式</BaseButton>
      <BaseButton class="btn" @handleClick="backToCarIndex">返回首頁</BaseButton>
    </div>
  </div>
</template>
<script>
export default {
  //實作prop切換input type，
  props: {
    formItems: {
      type: Array,
      required: true,
    },
    secondFormItems:{
      secondFormItems:{
        type:Array,
      }
    }
  },
  data(){
    return{
      mode:'main'
    }
  },
  computed: {
    modeFormItems() {
      if(this.mode==='main'){
        return this.formItems;
      }else{
        return this.secondFormItems;
      }
    },
  },
  methods:{
    backToCarIndex(){
      this.$router.push('/cars')
    },
    handleSubmit(){
      this.$emit('handleSubmit');
      this.backToCarIndex()
    },
    toggleMode(){
      if(this.mode==='main'){
          this.mode='second'
      }else{
        this.mode='main'
      }
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
  margin-top: 3rem;
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
  display:flex;
  flex-direction:column;
  row-gap:1rem;
  bottom: 5%;
  width: 50px;
  left: 92%;
  .btn{
    width:50px;
    height:50px;
  }
}
</style>

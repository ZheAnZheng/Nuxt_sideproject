<template>
  <Home/>
</template>

<script>
export default {
  name: "IndexPage",
  layout (context) {
    return 'main'
  }
};
</script>
<style lang="scss" >
@import "../assets/scss/reset.scss";
@import "../assets/scss/color.scss";
@import url('https://fonts.googleapis.com/css2?family=Smooch+Sans:wght@300;400;500;600;700;800;900&display=swap');
html,body{
  height:100%;
  width:100%;
}
body{
  font-family: 'Smooch Sans', sans-serif;
  font-size:16px;
}
#__nuxt,#__layout{
  height:100%;
}
.body-container{
  padding-top:100px;
  width:100%;
  height:100%;
}

</style>
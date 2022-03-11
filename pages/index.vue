<template>
  <Home />
</template>

<script>
export default {
  name: "IndexPage",
  layout(context) {
    return "main";
  },
};
</script>
<style lang="scss">
html,
body,
#__nuxt,
#__layout {
  height: 100%;
  width: 100%;
  .body-container {
    padding-top: 100px;
  }
}
</style>

<template>
  <div class="main-container">
    <Header />
    <div class="body-container">
      <Nuxt />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.main-container {
  height: 100%;
  width: 100%;
  background-color: var(--primary-bg-color);
}
.body-container {
  padding-top: 100px;
  width: 100%;
  height: 100%;
  background-color: var(--primary-bg-color);
}
</style>

<template>
  <header>
    <div>中古車網站</div>
    <div class="theme-toggle">
      <div class="swtich-road" :class="{ 'switch-on': isSwitchOn }">
        <div class="switch-ball" @click="toggleSwitch"></div>
      </div>
    </div>
  </header>
</template>
<script>
export default {
  data() {
    return {
      isSwitchOn: false,
      themeMode: "light",
    };
  },
  methods: {
    toggleSwitch() {
      this.isSwitchOn = !this.isSwitchOn;
      if (this.themeMode === "light") {
        this.themeMode = "dark";
        this.turnTheme(this.themeMode);
      } else {
        document.documentElement.setAttribute("data-theme", "light");
        this.themeMode = "light";
        this.turnTheme(this.themeMode);
      }
    },
    turnTheme(mode) {
      document.documentElement.setAttribute("data-theme", mode);
    },
  },
};
</script>
<style lang="scss">
header {
  position: fixed;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  height: 100px;
  font-size: 32px;
  line-height: 100px;
  padding: 0 2rem;
  background-color: var(--primary-bg-color);
  color: var(--primary-text-color);
  z-index: 100;
}
.theme-toggle {
  .swtich-road {
    position: relative;
    width: 100px;
    height: 30px;
    border-radius: 100px;
    box-shadow: inset 1px 1px 4px 0 rgba(0, 0, 0, 0.3);
    &::before {
      content: "";
      display: block;
      z-index: 150;
      width: 30%;
      border-radius: 100px;
      height: 30px;
      transition: all 0.2s ease;
      background: var(--primary-color);
    }
    &.switch-on::before {
      width: 100%;
    }
    &.switch-on .switch-ball {
      left: 70%;
    }
  }
  .switch-ball {
    display: inline-block;
    position: absolute;
    width: 30px;
    height: 30px;
    top: 0;
    left: 0;
    border-radius: 50%;
    background-color: var(--primary-bg-color);
    transition: all 0.2s;
    z-index: 999;
    box-shadow: inset -1px -1px 3px 0 rgba(0, 0, 0, 0.3);
    cursor: pointer;
  }
}
</style>

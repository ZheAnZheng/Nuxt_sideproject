<template>
  <div class="container">
    <div class="title">
      <TransitionGroup @afterEnter="addCount" name="fade" tag="div" appear>
        <span v-for="word in words" :key="word">{{ word }}</span>
      </TransitionGroup>
    </div>

    <transition name="btn" mode="out-in">
      <!-- loading-box 為了btn未出現時可以替補位置，讓版面不會突然變版 -->
      <div class="loading-box" v-if="isLoading"></div>
      <nuxt-link class="btn-wrapper" to="/cars" v-else>
        <baseButton> 進入網站 </baseButton>
      </nuxt-link>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      words: [],
      title: "歡迎進入中古車網站",
      count: 0,
      isLoading: true,
    };
  },
  mounted() {
    const splitWords = this.title.split("");
    this.words = [...splitWords];
  },
  watch: {
    // count到8表示所有動畫跑完
    count(val) {
      if (val === 8) {
        this.isLoading = false;
      }
    },
  },
  methods: {
    addCount() {
      this.count++;
    },
  },
};
</script>
<style lang="scss" scoped>
.title {
  font-size: 40px;
  span {
    display: inline-block;
    color: var(--primary-text-color);
  }
}
.btn-wrapper,
.loading-box {
  height: 3rem;
  width: 5rem;
}
.container {
  height: 100%;
  display: flex;
  row-gap: 3rem;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
@mixin setDelay() {
  $initDelay: 0.2s;
  @for $i from 1 through 9 {
    &:nth-child(#{$i}) {
      transition-delay: $initDelay;
    }
    $initDelay: $initDelay + 0.2s;
  }
}
.fade-enter {
  opacity: 0;
  transform: translateY(-200px);
}
.fade-enter-active {
  transition: all 1s cubic-bezier(0.38, 0.09, 0.37, 1.35);
  @include setDelay();
}
.fade-enter-to {
  opacity: 1;
  transform: translateY(0);
}
.btn-enter {
  opacity: 0;
}
.btn-enter-active {
  transition: all 0.2s ease-in;
}
.btn-enter-to {
  opacity: 1;
}
</style>

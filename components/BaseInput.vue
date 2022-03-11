<template>
  <div class="form-group">
    <div class="img-wrapper" v-show="inputData.type === 'file'">
      <img :src="image" />
    </div>
    <label>{{ inputData.name }}</label>
    <input
      v-if="!isSelect"
      :type="inputData.type"
      v-model="inputData.value"
      min="0"
      @change="handlechange"
    />

    <select v-else v-model="inputData.value" required>
      <option :selected="true" value="" disabled>請選擇</option>
      <option
        v-for="select in inputData.selectItems"
        :vlaue="select.value"
        :key="select.id"
      >
        {{ select.value }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    inputData: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      image: "",
    };
  },
  computed: {
    isSelect() {
      if (this.inputData.type === "select") {
        return true;
      } else {
        return false;
      }
    },
  },
  methods: {
    //因為只是本地的圖片，所以沒辦法真的新增圖片
    handlechange(e) {
      const { files } = e.target;
      if (!files) {
        return;
      }
      if (files.length > 0) {
        this.image = window.URL.createObjectURL(files[0]);
      } else {
        this.image = "";
      }
    },
  },
};
</script>
<style lang="scss" scoped>
.form-group {
  font-size: 2rem;
  label {
    display: block;
  }
}
.img-wrapper {
  background-color: var(--mute-color);
  height: 200px;
  width: 200px;
  float: right;
  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
input[type="number"],
input[type="text"] {
  outline: none;
  border: unset;
  height: 30px;
  border-bottom: 2px solid var(--primary-color);
  background-color: var(--primary-bg-color);
}
input[type="text"] {
  width: 50%;
}
select {
  &:invalid {
    color: var(--mute-color);
  }
}
</style>

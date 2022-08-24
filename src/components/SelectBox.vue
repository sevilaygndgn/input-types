<template>
  <div class="a-dropdown" :tabindex="tabindex" @blur="open = false">
    <div
      class="a-dropdown-item"
      @click="open = !open"
      :class="{ 'arrow-down': !open }"
    >
      {{ selected }}
      <svg
        class="arrow"
        width="14"
        height="10"
        viewBox="0 0 18 10"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M17 9L9 1L1 9"
          stroke="#202142"
          stroke-width="2"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
      </svg>
    </div>
    <div class="a-item-list" :class="{ 'select-hide': !open }">
      <div
        class="a-item"
        v-for="(option, i) in options"
        :key="i"
        @click="
          selected = option;
          open = false;
        "
      >
        {{ option }}
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    options: {
      type: Array,
      required: true,
    },
    default: {
      type: String,
      required: false,
      default: null,
    },
    tabindex: {
      type: Number,
      required: false,
      default: 0,
    },
  },
  data() {
    return {
      selected: this.default
        ? this.default
        : this.options.length > 0
        ? this.options[0]
        : null,
      open: false,
    };
  },
};
</script>
<style lang="scss" scoped>
.a-dropdown {
  position: relative;
  width: 100%;
  text-align: left;
  outline: none;
  width: 300px;
  line-height: 45px;
  color: #202142;
  background-color: #fff;
  font-family: "Poppins", sans-serif;
  &-item {
    display: flex;
    justify-content: space-between;
    border-radius: 10px;
    border: 1px solid #c3c3e4;
    padding-left: 1em;
    padding-right: 1em;
    font-size: 14px;
    cursor: pointer;
    &:hover {
      border: 1px solid #ee4878;
    }
    &.arrow-down {
      .arrow {
        transform: rotate(180deg);
      }
    }
    .arrow {
      margin-top: 20px;
    }
  }
  .a-item {
    padding-left: 1em;
    cursor: pointer;
    &:hover {
      background-color: #ee4878;
    }
    &-list {
      font-size: 12px;
      position: absolute;
      box-shadow: 0px 16px 45px -15px rgba(2, 5, 132, 0.25);
      left: 0;
      right: 0;
    }
  }
  .select-hide {
    display: none;
  }
}
</style>

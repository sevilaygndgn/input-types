<template>
  <div class="o-wrapper-tag">
    <label>Tags</label>
    <ul>
      <li
        v-for="index in tagList"
        :key="index"
        :index="index"
      >
        <span class="a-tag">{{ index }}</span>
        <button @click="deletedFunc(index)">
          <svg
            width="20"
            height="20"
            viewBox="0 0 24 25"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <g clip-path="url(#clip0_2_743)">
              <path
                d="M18 6.5L6 18.5"
                stroke="white"
                stroke-width="1.5"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <path
                d="M6 6.5L18 18.5"
                stroke="white"
                stroke-width="1.5"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </g>
            <defs>
              <clipPath id="clip0_2_743">
                <rect
                  width="24"
                  height="24"
                  fill="white"
                  transform="translate(0 0.5)"
                />
              </clipPath>
            </defs>
          </svg>
        </button>
      </li>
    </ul>
    <span class="a-text"
      >For example: fitness app, dashboard, navigation, webshop, landing
      page</span
    >
  </div>
</template>
<script>
import { eventBus } from "@/main";
export default {
  data() {
    return {
      tagList: [],
    };
  },
  methods: {
    deletedFunc: function (index) {
      this.tagList.splice(this.index, 1);

    },
  },
  created() {
    eventBus.$on("addedTags", (data) => {
      this.tagList.push(data);
    });
  },
};
</script>
<style lang="scss" scoped>
.o-wrapper-tag {
  width: 800px;
  height: 120px;
  display: grid;
  gap: 15px;
  label {
    font-family: "Merriweather", serif;
    font-weight: 900;
    font-size: 15px;
    color: #202142;
  }
  ul {
    border: 1px solid #c3c3e4;
    border-radius: 10px;
    width: 600px;
    height: 50px;
    padding: 10px;
    display: flex;
    align-items: center;
    column-gap: 10px;
    li {
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: #202142;
      color: #fff;
      padding: 10px;
      border-radius: 5px;
      font-family: "Poppins", sans-serif;
      .a-tag {
        margin-right: 5px;
      }
      button {
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #202142;
        border: none;
      }
    }
  }
  .a-text {
    font-family: "Poppins", sans-serif;
    font-style: normal;
    font-size: 12px;
    color: #202142;
  }
}
</style>

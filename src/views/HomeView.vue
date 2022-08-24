<template>
  <div class="o-container">
    <div class="o-wrapper">
      <label>Tags</label>
      <input
        v-model="tagsInput"
        placeholder="Add tags separated by comma"
        @change="emitAddedTags"
      />
      <span class="a-text"
        >For example: fitness app, dashboard, navigation, webshop, landing
        page</span
      >
    </div>
    <add-tags />
    <div class="m-category">
      <span class="m-category__title">Category</span>
      <select-box
        :options="['Web', 'Mobile', 'UI Kit', 'Coded', 'Other']"
        :default="'Select something'"
      />
    </div>
  </div>
</template>

<script>
import AddTags from "@/components/AddTags";
import SelectBox from "@/components/SelectBox";
import { eventBus } from "@/main";
export default {
  components: { AddTags, SelectBox },
  name: "HomeView",
  data() {
    return {
      tagsInput: "",
    };
  },
  methods: {
    emitAddedTags() {
      eventBus.$emit("addedTags", this.tagsInput);
    },
  },
};
</script>
<style lang="scss" scoped>
.o-container {
  background-color: #ffffff;
  display: grid;
  gap: 35px;
  .o-wrapper {
    width: 800px;
    height: 120px;
    display: grid;
    gap: 15px;
    color: #202142;
    label {
      font-family: "Merriweather", serif;
      font-weight: 900;
      font-size: 15px;
    }
    input {
      width: 700px;
      height: 50px;
      border-radius: 10px;
      padding-left: 10px;
      font-family: "Poppins", sans-serif;
      border: 1px solid #c3c3e4;
      &:focus {
        outline: none;
      }
    }
    .a-text {
      font-family: "Poppins", sans-serif;
      font-style: normal;
      font-size: 12px;
    }
  }
  .m-category {
    display: grid;
    gap: 15px;
    color: #202142;
    .m-category__title {
      font-family: "Merriweather", serif;
      font-weight: 900;
      font-size: 15px;
    }
  }
}
</style>

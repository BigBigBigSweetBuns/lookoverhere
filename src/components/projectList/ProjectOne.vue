<template>
  <div class="ProjectOne">
    <div class="text">
      <p class="title">{{ title }}</p>
      <p class="desc">{{ desc }}</p>
    </div>
    <div class="logo">
    </div>
  </div>
</template>

<script>
export default {
  name: "ProjectOne",
  props: ["title", "desc"],
  data: function () {
    return {};
  },
};
</script>
<style lang="scss" scoped>
@import "@/assets/variable.scss";
.ProjectOne {
  display: flex;
  align-items: center;
  width: 100%;
  height: $font-size-content * 6 + $padding * 2;
  background-color: #ffffff;
  box-sizing: border-box;
  border-radius: $border-radius * 2;
  padding: $padding;
  position: relative;
  .logo {
    width: 20%;
    background-color: #666;
    border: 1px solid #ccc;
    border-radius: $border-radius;
    position: relative;
    &:before {
      content: "";
      display: block;
      padding-top: 100%;
    }
    .content {
      position: absolute;
      width: 100%;
      height: 100%;
    }
  }
  .text {
    width: 80%;
    color: $color-semi;
    p {
      padding: 0;
      margin: 0;
      line-height: 1.2;
    }
    .title {
      color: $color-semi;
      font-weight: bold;
      font-size: $font-size-title;
      line-height: 1.5;
    }
    .desc {
      color: $color-gray;
      font-size: $font-size-content;
    }
  }
}
</style>
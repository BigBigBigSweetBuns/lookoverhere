<template>
  <div class="home">
    <TopHeader></TopHeader>
    <img alt="Vue logo" src="../assets/logo.png" />
    <ProjectList></ProjectList>
  </div>
</template>

<script>
// @ is an alias to /src

import TopHeader from "@/components/topHeader/TopHeader.vue";
import ProjectList from "@/components/projectList/ProjectList.vue";

export default {
  name: "Home",
  components: {
    TopHeader,
    ProjectList,
  },
};
</script>
<style lang="scss" scoped>
.home {
  width: 100%;
  max-width: 1920px;
  height: 1080px;
  border: 1px solid #000;
  margin: auto;
  position: relative;
}
</style>

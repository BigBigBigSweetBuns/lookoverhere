<template>
  <div class="home">
    <TopHeader></TopHeader>
    <img alt="Vue logo" src="../assets/logo.png" />
    <ProjectList></ProjectList>
    <AboutMe></AboutMe>
  </div>
</template>

<script>
// @ is an alias to /src

import TopHeader from "@/components/topHeader/TopHeader.vue";
import ProjectList from "@/components/projectList/ProjectList.vue";
import AboutMe from "@/components/aboutMe/AboutMe.vue";

export default {
  name: "Home",
  components: {
    TopHeader,
    ProjectList,
    AboutMe,
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

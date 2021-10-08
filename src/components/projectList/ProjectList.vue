<template>
  <div class="ProjectList">
    <div class="header">
      <ul class="navbar">
        <li
          v-for="(navbar, index) in navbarList"
          :key="index"
          :ref="navbar.name"
          @mouseover="onHandleOver($event, index)"
          @mouseleave="onHandleLeave()"
          @click="onHandleClick($event, index)"
          :class="{ active: activeIndex === index }"
        >
          {{ navbar.title }}
        </li>
      </ul>
      <div
        class="border"
        :style="{
          width: navbarBorder.width + 'px',
          left: navbarBorder.left + 'px',
        }"
      ></div>
      <div class="close">
        <i class="icon">X</i>
      </div>
    </div>
    <div class="project-list">
      <div v-for="(showProject, idx) in showList" :key="idx">
        <ProjectOne
          :desc="showProject.desc"
          :title="showProject.title"
          :imgUrl="showProject.imgUrl"
        ></ProjectOne>
      </div>
    </div>
  </div>
</template>

<script>
import ProjectOne from "./ProjectOne.vue";
export default {
  components: {
    ProjectOne,
  },
  // props: [{}],
  data() {
    return {
      navbarList: [
        {
          name: "ProjectList",
          title: "项目列表",
        },
        {
          name: "AboutMe",
          title: "关于我",
        },
        {
          name: "AboutMe",
          title: "关于我",
        },
        {
          name: "AboutMe",
          title: "关于我",
        },
      ],
      showList: [
        {
          imgUrl: "",
          title: "你好",
          desc: "这里是描述",
        },
        {
          imgUrl: "",
          title: "你好",
          desc: "这里是描述description,new description",
        },
        {
          imgUrl: "",
          title: "你好",
          desc: "这里是描述description,new description",
        },
        {
          imgUrl: "",
          title: "你好",
          desc: "这里是描述description,new description",
        },
        {
          imgUrl: "",
          title: "bookkeeping",
          desc: "这里是描述description,description",
        },
      ],
      activeIndex: 0,
      lastActiveIndex: 0,
      navbarBorder: {
        left: 0,
        width: 0,
        lastLeft: 0,
        lastWidth: 0,
      },
    };
  },
  mounted() {
    this.setNavbar();
  },
  methods: {
    onHandleOver({ target }, index) {
      const { width, left } = target.getBoundingClientRect();
      const { left: parentLeft } = target.parentNode.getBoundingClientRect();
      this.navbarBorder.lastWidth = this.navbarBorder.width;
      this.navbarBorder.lastLeft = this.navbarBorder.left;
      this.navbarBorder.width = width;
      this.navbarBorder.left = left - parentLeft;
      this.lastActiveIndex = this.activeIndex;
      this.activeIndex = index;
    },
    onHandleClick({ target }, index) {
      const { width, left } = target.getBoundingClientRect();
      const { left: parentLeft } = target.parentNode.getBoundingClientRect();
      this.navbarBorder.lastWidth = width;
      this.navbarBorder.lastLeft = left - parentLeft;
      this.navbarBorder.width = width;
      this.navbarBorder.left = left - parentLeft;
      this.lastActiveIndex = index;
      this.activeIndex = index;
    },
    onHandleLeave() {
      this.navbarBorder.left = this.navbarBorder.lastLeft;
      this.navbarBorder.width = this.navbarBorder.lastWidth;
      this.activeIndex = this.lastActiveIndex;
    },
    setNavbar() {
      const dom = this.$refs[this.navbarList[0].name];
      const { width } = dom.getBoundingClientRect();
      this.navbarBorder.width = width;
      console.log(dom);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/variable.scss";
.ProjectList {
  max-width: 1080px;
  background-color: #eeeeee;
  padding: $font-size-content / 2;
  position: absolute;
  // bottom: -100%;
  .header {
    // display: flex;
    padding: $font-size-content / 2;
    position: relative;
    .navbar {
      width: 100%;
      display: flex;
      font-size: $font-size-title;
      list-style-type: none;
      margin: 0 5rem 0 0;
      padding-left: 0;
      li {
        cursor: pointer;
        line-height: 1.5;
        color: $color-light;
        margin-right: 1em;
        transition: color 0.5s;
      }
      .active {
        color: $color-semi;
      }
    }
    .close {
      width: $font-size-content;
      height: $font-size-content;
      background-color: $bg-color-semi;
      border-radius: $border-radius;
      padding: 0.1rem;
      position: absolute;
      right: $font-size-content / 2;
      top: $font-size-content / 2;
      i {
        display: block;
        color: $color-white;
        font-size: $font-size-content;
        font-style: initial;
        text-align: center;
        line-height: 1;
      }
    }
    .border {
      width: 100%;
      height: 3px;
      background: #353535;
      border-radius: 3px;
      position: relative;
      left: 0;
      top: 0;
      transition: left 0.5s, width 0.5s;
    }
  }
  .project-list {
    display: flex;
    flex-wrap: wrap;
    margin: 0.5rem 0;
    & > div {
      width: calc(25% - 1rem);
      margin: 0.5rem;
    }
  }
}
</style>

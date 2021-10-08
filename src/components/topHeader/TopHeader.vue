<template>
  <div class="TopHeader">
    <div class="content">
      <div class="logo">
        <a href="#" target="_blank" rel="noopener noreferrer"></a>
      </div>
      <div class="menu">
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
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TopHeader",
  data() {
    return {
      navbarList: [
        {
          name: "home",
          title: "主页",
        },
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
          title: "简历",
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
.TopHeader {
  width: 100%;
  background-color: rgba($color: #000000, $alpha: 0.3);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 2;

  .content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    max-width: 1920px;
    height: $font-size-content * 8;
    padding: $font-size-content * 2;
    box-sizing: border-box;

    .logo {
      width: auto;
      min-width: 10rem;
      height: $font-size-content * 4;
      background-color: #aaa;
    }

    .menu {
      display: flex;
      justify-content: flex-end;
      position: relative;
      .navbar {
        display: flex;
        font-size: $font-size-head;
        list-style-type: none;
        margin: 0 2em 0 0;
        padding-left: 0;
        li {
          cursor: pointer;
          color: $color-light;
          line-height: 2;
          margin-right: 2em;
          transition: color 0.5s;
          &:last-child {
            margin-right: 0;
          }
        }
        .active {
          color: $color-semi;
        }
      }
      .border {
        width: 100%;
        height: 2px;
        background: #353535;
        border-radius: 3px;
        position: absolute;
        left: 0;
        bottom: $font-size-head / 10;
        transition: left 0.5s, width 0.5s;
      }
    }
  }
}
</style>
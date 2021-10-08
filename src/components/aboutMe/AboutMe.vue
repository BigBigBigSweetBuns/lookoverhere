<template>
  <div class="AboutMe">
    <div class="inner">
      <div class="aboutme-top">
        <div class="title">你好!</div>
        <div class="contact-drawer">
          <a class="phone" :href="`tel:${telephone}`">{{ telephone }}</a>
          <a class="mail" :href="`mailto:${mail}`">{{ mail }}</a>
        </div>
      </div>
      <div class="aboutme-bottom">
        <div class="website-record">
          <p>网站制作者: 黄明康</p>
          <a href="http://beian.miit.gov.cn" target="_blank"
            >粤ICP备18149108号</a
          >
        </div>
        <div class="menu-social-links">
          <ul>
            <li>
              <a href="https://leetcode-cn.com/u/dou-sha-bao-n/" target="_blank"
                ><i class="iconfont icon-leetcode"></i
              ></a>
            </li>
            <li>
              <a href="https://github.com/BigBigBigSweetBuns" target="_blank"
                ><i class="iconfont icon-github"></i
              ></a>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <botton class="botton-close">
      <span class="botton-circle"></span>
      <i class="iconfont icon-close"></i>
    </botton>
  </div>
</template>

<script>
export default {
  name: "AboutMe",
  data() {
    return {
      telephone: "18676932231",
      mail: "dadadadoushabao@163.com",
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/variable.scss";
.AboutMe {
  background-color: #eee;
  padding: 0 $font-size-content * 4;
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;

  a {
    color: #454545;
    text-decoration: none;
  }

  .inner {
    padding: $font-size-content * 5 0;

    .aboutme-top {
      display: flex;

      .title {
        width: $font-size-head * 15;
        font-size: $font-size-head * 5;
      }

      .contact-drawer {
        font-size: $font-size-head * 2;
        margin-top: $font-size-content * 3;

        a {
          display: block;
          line-height: 1.5;
          transition: $transition-default;
          &:hover {
            color: $red;
          }
        }
      }
    }

    .aboutme-bottom {
      display: flex;
      justify-content: space-between;
      align-items: center;

      .website-record {
        font-size: $font-size-description;
        letter-spacing: $font-size-description * 0.05;
      }

      .menu-social-links {
        > ul {
          list-style-type: none;
          padding-left: 0;
          margin: 0;
          display: flex;
          li {
            display: block;
            padding: $font-size-content;
            .iconfont {
              font-size: $font-size-content * 1.5;
              transition: $transition-default;
              &:hover {
                color: $red;
              }
            }
          }
        }
      }
    }
  }
  .botton-close {
    width: $font-size-content * 5;
    height: $font-size-content * 5;
    position: absolute;
    top: -$font-size-content * 2.5;
    right: $font-size-content * 4;
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
    .botton-circle {
      display: block;
      content: "";
      width: 100%;
      background: #454545;
      border-radius: 50%;
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      transition: $transition-default;
    }

    i {
      color: $white;
      font-size: $font-size-content * 1.5;
      z-index: 1;
      transform: rotate(30deg);
      transition: $transition-default;
    }

    &:hover {
      .botton-circle {
        transform: scale(110%, 110%);
      }
      i {
        transform: rotate(30+45+15deg);
      }
    }
  }
}
</style>
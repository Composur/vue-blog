<template>
  <section class="order">
    <HeaderTop title="订单列表" />
    <section class="order_no_login">
      <img src="./images/person.png" />
      <h3>登录后查看外卖订单</h3>
      <common-btn @click="login">立即登录</common-btn>
      <!-- <button @click="login">立即登陆</button> -->
    </section>
  </section>
</template>

<script>
import { Indicator } from "mint-ui";
import CommonBtn from "../../components/CommonBtn";
import HeaderTop from "../../components/HeaderTop/HeaderTop";
export default {
  data() {
    return {
      userInfo: {}
    };
  },
  methods: {
    login() {
      Indicator.open({
        text: "保留模块...",
        spinnerType: "fading-circle"
      });
      this.timer = setTimeout(() => {
        Indicator.close();
      }, 1000);
    }
  },
  beforeDestroy() {
    if (this.timer) {
      clearTimeout(this.timer);
    }
  },
  components: {
    HeaderTop,
    "common-btn": CommonBtn
  }
};
</script>


<style lang="stylus" rel="stylesheet/stylus">
@import '../../common/stylus/mixins.styl';

.order { // 订单
  width: 100%;

  .header {
    background-color: #02a774;
    position: fixed;
    z-index: 100;
    left: 0;
    top: 0;
    width: 100%;
    height: 45px;

    .header_search {
      position: absolute;
      left: 15px;
      top: 50%;
      transform: translateY(-50%);
      width: 10%;
      height: 50%;

      .icon-sousuo {
        font-size: 25px;
        color: #fff;
      }
    }

    .header_title {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 50%;
      color: #fff;
      text-align: center;

      .header_title_text {
        font-size: 20px;
        color: #fff;
        display: block;
      }
    }

    .header_login {
      font-size: 14px;
      color: #fff;
      position: absolute;
      right: 15px;
      top: 50%;
      transform: translateY(-50%);

      .header_login_text {
        color: #fff;
      }
    }
  }

  .order_no_login {
    padding-top: 140px;
    width: 60%;
    margin: 0 auto;
    text-align: center;

    >img {
      display: block;
      width: 100%;
      height: 30%;
    }

    >h3 {
      padding: 10px 0;
      font-size: 17px;
      color: #6a6a6a;
    }

    >button {
      display: inline-block;
      background: #02a774;
      font-size: 14px;
      color: #fff;
      border: 0;
      outline: none;
      border-radius: 5px;
      padding: 10px 20px;
    }
  }
}
</style>
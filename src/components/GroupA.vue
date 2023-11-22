<template>
  <div id="groupA">

    <!-- SEND Start -->

    <transition name="show">
      <template v-if="isRight">
        <button class="send" @click="send">
          <span class="text">Send</span>
          <div class="yinyingb"></div>
        </button>
      </template>
    </transition>


    <!-- SEND End -->

    <!-- MESSAGE Start -->
    <div id="group2">
      <div class="message" :class="{ 'big1': isRight }">
        <span class="message-text"></span>
        <span class="vertical-line" v-if="isRight"></span>
        <input type="text" placeholder="What can i do for you?" v-if="isRight" ref="input">
      </div>
    </div>
    <div class="yinyinga" :class="{ 'big2': isRight }">
    </div>
    <!-- MESSAGE End -->
  </div>
</template>

<script>
export default {
  name: 'GroupA',
  data() {
    return {
        isRight: false,
    };
  },
  methods: {
    send() {
      if(this.$refs.input.value==="Where are you from?") {
        alert("ok,输入正确，进入下一步")
      } else {
        alert("输出错误")
      }
    }
  },
  mounted() {
    setInterval(() => {
      this.isRight = true;
    }, 1000);
  }
};
</script>

<style lang="less" scoped>
.send {
  position: absolute;
  width: 87px;
  height: 39px;
  left: 1262px - 901;
  top: 0;
  background: linear-gradient(100.5deg, #A6D1FE -30.06%, #182CEE 135.88%);
  border-radius: 10px;
  border: none;
  /* Send */
  z-index: 99;
  cursor: pointer;
  .text {
    /* Send */
  position: absolute;
  width: 36px;
  height: 22px;
  left: 1288px - 1262;
  top: 919px - 911;

  font-family: 'Rounded Mplus 1c';
  font-style: normal;
  font-weight: 800;
  font-size: 15px;
  line-height: 22px;

  color: #FFFFFF;
  z-index: 100;

  }

  .yinyingb {
  position: absolute;
  width: 66px;
  height: 32px;
  left: 11px;
  top: 6px;
  background: linear-gradient(90deg, #449BF8 -38.51%, #1C30F2 133.91%);
  filter: blur(15px);
  z-index: 98;
}
}

// 淡入淡出
.show-enter-active {
  transition: all 1.5s;
}
.show-enter {
  opacity: 0;
}

#group2 {

  z-index: 1;

  position: absolute;
  width: 477px;
  height: 68px;
  left: 0;
  top: 14px;

  .message {
    position: absolute;
    width: 58px;
    height: 58px;
    right: 0px;
    top: 0px;
    background: rgba(39, 41, 53, 0.8);
    border-radius: 10px;
    transition: width 2s;
    /* 添加过渡效果 */
    .message-text {
      position: absolute;
      width: 24px;
      height: 24px;
      left: 918px - 901;
      top: 17px;
      background: url(../assets/message-text.png) no-repeat;
    }
    .vertical-line {
      /* Line 1 */
      position: absolute;
      width: 13px;
      height: 0px;
      left: 956px - 901;
      top: 29px;

      border: 1px solid rgba(255, 255, 255, 0.3);
      transform: rotate(90deg);

    }

    input {
      /* Where are you from? */
      position: absolute;
      width: 250px;
      height: 19px;
      left: 975px - 901;
      top: 944px - 925;

      background: transparent;
      border: none;
      outline: none;

      font-family: 'Rounded Mplus 1c';
      font-style: normal;
      font-weight: 500;
      font-size: 16px;
      line-height: 117%;
      /* identical to box height, or 19px */
      color: rgba(255, 255, 255, 0.9);

      &::placeholder {
      color: rgba(255, 255, 255, 0.4);
      }
    }
  }

  .big1 {
    width: 477px;
    /* 添加宽度变化 */
  }
}
.yinyinga {
  /* Rectangle 4 */

  position: absolute;
  width: 43px;
  height: 58px;
  right: 422px + 956 - 1328 - 43;
  bottom:0px;

  background: #272935;
  filter: blur(15px);
  border-radius: 10px;
  transition: width 2s;
  z-index: 0;

}
.big2 { 
  width: 459px;
}
</style>

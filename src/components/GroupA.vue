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
    <div id="group2" >

      <div class="message" :style="{ height: Height + 'px' ,width: Width + 'px' }">

        <div class="fullscr" v-if="isClick4" @click="fullScreen">
          <img src="../assets/arrow.png" alt="">
          <span>Full screen</span>
        </div>
        <div class="answer" v-if="isClick3">
          <div class="cover" :class="{ 'full': isFull }"></div>
          <div class="answerblock" >
            I am come from China, i was designed<br>
            to serve people better.
          </div>
        </div>
        <span class="message-text"></span>
        <span class="vertical-line" v-if="isRight"></span>
        <transition name="show">
          <input type="text" placeholder="What can i do for you?" v-if="isRight2" ref="input">
        </transition>
        <transition name="show">
          <div class="horizontal-line" v-if="isClick" :class="{'long':isFull}"></div>
        </transition>
        <transition name="show">
          <div class="askMessage" v-if="isClick2" :style="{bottom:Bottom + 'px'}">{{ askMessage }}</div>
        </transition>
        
      </div>
    </div>
      
    <div class="yinyinga" :class="{ 'big1': isRight ,'big2':isFull}">
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
        isRight2: false,
        isAnswer: false,
        Height:58,
        Width:58,

        Bottom:100,
        isClick:false,
        isClick2:false,
        isClick3:false,
        isClick4:false,
        isFull:false,
        askMessage: '',
    };
  },
  methods: {
    send() {
      if(this.$refs.input.value==="Where are you from?") { // 这里为了演示效果要求输入内容固定才会触发接下来的动画，要是输入不对，不做处理
        this.Height=157
        this.askMessage =this.$refs.input.value
        this.$refs.input.value="",
        this.isClick = true
        setTimeout(() => {
          this.isClick2 = true
        }, 500);

        setTimeout(() => {
          this.isClick3=true
          this.isClick4=true
          this.Height=212
          this.Bottom=152
        }, 500)
      } 
    },
    fullScreen() {
      this.isFull=true
      this.Height=941
      this.Width=1320

      this.isClick4=false

    }
  },
  mounted() {
    setTimeout(() => {
      this.isRight = true;
      this.Width=477
    }, 500);
    this.$nextTick(() => {
      this.$refs.input.focus();
      if (this.isClick2) {
        setTimeout(() => {
          this.isClick3 = true;
        }, 500);
      }
    });
    setTimeout(() => {
      this.isRight2 = true;
    }, 1000);

  }
};
</script>

<style lang="less" scoped>
* {
  margin: 0px;
  padding: 0px;
}
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
  z-index: 100;
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
  transition: all 0.5s;
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
    bottom: 0px;
    background: rgba(39, 41, 53, 0.8);
    border-radius: 10px;
    transition: all .5s;
    /* 添加过渡效果 */
    .fullscr {
    position: absolute;
    width: 68px;
    height: 12px;
    left: 1288px - 901;
    top: 789px - 771;
    cursor: pointer;
    img {
      position: absolute;
      width: 8.25px;
      height: 8.25px;
      top: 2.75px;

    }
    span {
      position: absolute;
      top: 0;
      width: 52px;
      height: 12px;
      left: 12px;

      font-family: 'Rounded Mplus 1c';
      font-style: normal;
      font-weight: 500;
      font-size: 10px;
      line-height: 12px;
      /* identical to box height, or 12px */

      color: rgba(255, 255, 255, 0.4);
    }
  }
  .answer {
    /* Rectangle 6 */

    position: absolute;
    width: 477px;
    height: 58px;
    left: 0px;
    bottom:  771px + 212 - 840 - 58;

    
    .cover {
      width: 100%;
      height: 100%;
      background: rgba(44, 46, 57, 0.4);

      
    }
    .full {
      width: 1440px;
      height: 1024px;
      transform: translate(-58px,-849px);
      transition: all .5s;
    }

    .answerblock {
      position: absolute;
      width: 100%;
      height: 38px;

      padding-left: 8.5px;

      font-family: 'Rounded Mplus 1c';
      font-style: normal;
      font-weight: 500;
      font-size: 16px;
      line-height: 117%;
      /* or 19px */

      color: rgba(255, 255, 255, 0.9);

      top: 9px;
      left: 16.5px;
      border-left: 3px solid #FFD600;

    }

  }
  .askMessage {
  /* Where are you from? */

  position: absolute;
  width: 170px;
  height: 19px;
  right: 901px + 477 - 1199 - 157;
  bottom: 100px;
  font-family: 'Rounded Mplus 1c';
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 19px;
  /* identical to box height, or 19px */

  color: rgba(255, 255, 255, 0.9);
  z-index: 1000;
  transition: all .5s;

}
    .message-text {
      position: absolute;
      width: 24px;
      height: 24px;
      left: 918px - 901;
      bottom: 17px;
      background: url(../assets/message-text.png) no-repeat;
    }
    .vertical-line {
      /* Line 1 */
      position: absolute;
      width: 13px;
      height: 0px;
      left: 956px - 901;
      bottom: 29px;

      border: 1px solid rgba(255, 255, 255, 0.3);
      transform: rotate(90deg);

    }

    input {
      /* Where are you from? */
      position: absolute;
      width: 250px;
      height: 19px;
      left: 975px - 901;
      bottom: 944px - 925;

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
  transition: width .5s;
  z-index: 0;

}
.horizontal-line {
  position: absolute;
  width: 438px;
  height: 0px;
  left: 918px - 901;
  bottom: 58px;

  border: 1px solid rgba(255, 255, 255, 0.5);
  z-index: 99;
  transition: all .5s;
}
.long {
  width: 1278px;
  
}
.big1 { 
  width: 459px;
}
.big2 {
  width: 1249px;
}
</style>

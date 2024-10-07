<template>
    <div class="inner" v-if="isTextHidden">
        <div class="text" @load="onLoaded" :style='textStyle'>
           <div class="text__inner">Крокодил Крейга - это социальная игра, направленная на развитие навыков взаимодействия. В игре принимают участие 2 человека, они получают карту социальной ситуации, согласно которой должны отыгрывать своего персонажа. Но не всё так просто. Помимо ситуации они получают социальный "эффект". Это может быть как определённая психологическая защита, так и роль для взаимодействия. Если зрители за минуту смогли угадать эффект, то игроки получают по одному баллу. В остальном правила ничем не ограничены. Have fun and enjoy your time spent on this game!</div>
          <button @click="textHidden(); sendValue();">далее</button>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      message: 'Hello, Craig!',
      textStyle: {},
      isTextHidden: true,
			inputValue: true,
    }
  },
  created() {
    setTimeout(() => {
      this.textAnimation();
    }, 50)
  },
  methods: {
    textAnimation() {
      this.textStyle = { transform: 'translateY(-100vh)' };
    },
    textHidden() {
			this.textStyle = { transform: 'translateY(-200vh)', transition: 'all 1s linear' };
			setTimeout(() => {
      	this.isTextHidden = false;
    	}, 1000)
    },
		sendValue() {
			setTimeout(() => {
      	this.$emit('send-data', this.inputValue);
    	}, 1500)
		}
  },
};
</script>

<style scoped>
    .inner {
      height: calc(100vh - 100px);
      width: 100%;
      position: relative;
      overflow: hidden;
    }
    .text {
      width: 100%;
      height: 100%;
      text-align: center;
      margin-top: 100vh;
      transform: translateY(-100px);
      transition: all 10s linear;
      display: flex;
      flex-direction: column;
      justify-content: space-around;
    }
    button {
      margin: 0 auto;
		  display: block;
		  border: 2px solid transparent;
		  padding: 20px;
		  font-weight: bold;
		  text-transform: uppercase;
		  cursor: pointer;
		  border-radius: 10px;
		  transition: all 1s ease;
    }
    
</style>
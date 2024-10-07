<template>
  <div class="inner">
<!--       <h1> Случайное событие {{ title }} </h1> -->
      <div class="card__inner" :style="cardsInner">
          <img v-if="firstImage" :src="firstImage" alt="Случайная картинка" id="image" :class="{'fade-out':imageFadingOut, 'fade-in':!imageFadingOut}" :style='imageStyle'>
          <img v-if="secondImage" :src="secondImage" alt="Случайная картинка" id="image" :class="{'fade-out':imageFadingOut, 'fade-in':!imageFadingOut}" :style='imageStyle'>
      </div>
      <button @click="changeTitle(); showRandomImage();" id="buttonGenerate" v-if="buttonVisible" :style="buttonStyle">генерация</button>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        images: [
          'src/images/image1.jpg',
          'src/images/image2.jpg',
          'src/images/image3.jpg',
        ],
        firstImage: '',
        secondImage: '',
        title: '',
        buttonVisible: true,
        isFading: false,
        imageFadingOut: false,
        imageFirstShow: true,
        imageSecondShow: true,
        imageStyle: {},
        cardsInner: {},
        buttonStyle: {},
      };
    },
    methods: {
      // change title on random number function
      changeTitle() {
        const randomNumber = Math.floor(Math.random()*101);
        console.log(randomNumber);
        this.title = randomNumber;
        document.title = randomNumber;
      },
      // show random image function
      showRandomImage() {
        this.imageFadingOut = true;
        if (this.imageFirstShow) {
          let randomImageIndex = Math.floor(Math.random() * this.images.length);
          this.firstImage = this.images[randomImageIndex];
          this.imageFadingOut = false;
          setTimeout(() => {
            this.imageFirstShow = false;
            this.imageFadingOut = false;
            this.cardsInner = { flexGrow: '1', maxHeight: 'fit-content'}
            this.imageStyle = { position: 'relative', height: 'calc(100vh - 200px)' };
          }, 100);
        } else if (this.imageSecondShow) {
            setTimeout(() => {
              this.imageStyle = {position: 'relative', height: 'auto',  maxWidth: '0px', opacity: '0'};
              this.cardsInner = { flexGrow: '1', maxHeight: 'calc(100vh - 160px)', display: 'grid', gridTemplateColumns: '1fr 1fr' }
              let randomImageIndex = Math.floor(Math.random() * this.images.length);
              this.secondImage = this.images[randomImageIndex];
              setTimeout(() => {
                this.imageStyle = {position: 'relative', height: 'auto', maxWidth: 'calc(50vw - 210px)', opacity: '1'};
              }, 50);
              this.imageFadingOut = false;
              this.imageSecondShow = false;
            }, 1000);
          } else {
            setTimeout(() => {
                this.imageStyle = { position: "relative", height: 'auto', maxWidth: '0px' };
                this.cardsInner = { flexGrow: '1', maxHeight: '0px', display: 'grid', gridTemplateColumns: '1fr 1fr' };
              }, 50);
            setTimeout(() => {
              this.firstImage = '';
              this.secondImage = '';
              this.imageStyle = {};
              this.cardsInner = {}
              this.imageFirstShow = true;
              this.imageSecondShow = true; 
            }, 3000);
        }
      },
      // hide button function
      hideButton() {
        this.buttonVisible = false;
      },
    }
  }
</script>
<style scoped>
  .inner{
    min-height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    position: relative;
    transition: all 1s linear;
    flex-grow: 1;
    opacity: 0;
  }
  h1{
    text-align: center;
  }
  p{
    text-align: center;
    margin-top: 40px;
  }
  button{
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
  img{
    width: auto;
    height: auto;
    display: block;
    margin: auto;
    border-radius: 40px;
    transition: all 1s ease;
    opacity: 0;
    height: 0;
    position: absolute;
  }
  .card__inner{
    max-height: 0px;
    transition: all 1s ease;
    gap: 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .item{
    flex-grow: 1;
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .fade-out {
    opacity: 0;
    max-width: 0;
  }
  .fade-in {
    opacity: 1;
    max-width: 100%;
  }
  
</style>

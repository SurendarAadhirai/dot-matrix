<template>
  <!-- 
    <div class="container1">
      content1
    </div>
    <br>
    <div class="container1">
      content2
    </div>
  </div> -->
  <div class="home-container">
  <div class="carousel-wrapper">
    <Carousel
      :items-to-show="1"
      :wrap-around="true"
      :mouse-drag="true"
      :touch-drag="true"
      class="custom-carousel"
    >
      <Slide v-for="(img, idx) in images" :key="idx">
        <img :src="img" class="carousel-image" @click="clickedImage(idx)"/>
      </Slide>
      <template #addons>
        <Navigation />
      </template>
    </Carousel>
  </div>
</div>
</template>

<script>
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Navigation } from 'vue3-carousel'
import img1 from '../assets/01.jpg'
import img2 from '../assets/02.jpg'
import img3 from '../assets/03.jpg'
import img4 from '../assets/04.jpg'
import img5 from '../assets/05.jpg'
export default {
  name: 'HelloWorld',
  components: {
    Carousel,
    Slide,
    Navigation
  },
  props: {
    msg: String
  },
  data () {
    return {
      images : [
  img1, img2, img3, img4, img5
]
    }
  },
  methods: {
    clickedImage (index) {
      console.log(index)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.home-container {
  margin-top: 5
}
.carousel-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 50vh; /* Full viewport height */
}

.custom-carousel {
  width: 80%; /* 80% of viewport width */
  height: 25rem;
  box-shadow: 0 8px 24px rgba(0,0,0,0.22), 0 1.5px 4px rgba(0,0,0,0.18);
  }

.carousel-image {
  width: 100%;
  height: auto;
  display: block;
  border-radius: 12px;
  object-fit: cover;
  object-fit: cover;
  border-radius: 12px;
  display: block;
}
.carousel__slide {
  transition: opacity 0.5s, transform 2s;
}
.carousel__slide--active {
  opacity: 1;
  transform: scale(1);
}
.carousel__slide:not(.carousel__slide--active) {
  opacity: 0;
  transform: scale(2);
  pointer-events: stroke;
}
@media screen and (max-width: 575px) {
  .custom-carousel {
  width: 100%; /* 80% of viewport width */
  height: 16rem;
  }
}
</style>

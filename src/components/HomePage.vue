<template>
    <div class="home">
      <Navbar />
  
      <div class="slideshow-container">
        <div v-for="(slide, index) in slides" :key="index" v-show="currentSlide === index" class="slide">
          <img :src="slide.image" :alt="'Slide ' + (index + 1)" />
        </div>
        <button class="prev" @click="prevSlide">&#10094;</button>
        <button class="next" @click="nextSlide">&#10095;</button>
      </div>
    </div>
  </template>
  
  <script>
  import Navbar from '@/components/NavBar.vue';
  
  export default {
    components: {
      Navbar
    },
    data() {
      return {
        currentSlide: 0,
        slides: [
          { image: require('@/assets/slide1.jpg') },
          { image: require('@/assets/slide2.jpg') },
          { image: require('@/assets/slide3.jpg') },
        ]
      };
    },
    methods: {
      nextSlide() {
        this.currentSlide = (this.currentSlide + 1) % this.slides.length;
      },
      prevSlide() {
        this.currentSlide = (this.currentSlide - 1 + this.slides.length) % this.slides.length;
      }
    },
    mounted() {
      setInterval(() => {
        this.nextSlide();
      }, 3000); // Change slide every 3 seconds
    }
  };
  </script>
  
  <style scoped>
  .home {
    margin-top: 70px; /* To offset the navbar */
  }
  
  .slideshow-container {
    position: relative;
    width: 100%;
    max-width: 1000px;
    margin: auto;
    overflow: hidden;
  }
  
  .slide img {
    width: 100%;
    height: auto;
  }
  
  .prev, .next {
    cursor: pointer;
    position: absolute;
    top: 50%;
    padding: 16px;
    margin-top: -22px;
    color: white;
    font-weight: bold;
    font-size: 18px;
    background-color: rgba(0, 0, 0, 0.5);
    border: none;
    border-radius: 50%;
    transition: 0.6s ease;
  }
  
  .prev {
    left: 10px;
  }
  
  .next {
    right: 10px;
  }
  
  .prev:hover, .next:hover {
    background-color: rgba(0, 0, 0, 0.8);
  }
  </style>
  
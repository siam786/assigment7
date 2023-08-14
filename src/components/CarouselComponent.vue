<script setup>
import { onBeforeUnmount, onMounted, ref } from "vue";
let carousel = null;
const images = ref([
  "https://images.pexels.com/photos/2518893/pexels-photo-2518893.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
  "https://images.pexels.com/photos/4702634/pexels-photo-4702634.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
  "https://images.pexels.com/photos/5677794/pexels-photo-5677794.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
  "https://images.pexels.com/photos/6341944/pexels-photo-6341944.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
]);

onMounted(() => {
  carousel = new Flickity(".main-carousel", {
    autoPlay: 3000, // Set autoplay duration to 3 seconds (3000 milliseconds)
  });
});

onBeforeUnmount(() => {
  alert("carousel destroy successfully");
  carousel.destroy();
});
</script>
<template>
  <h1>This is Carousel Component</h1>
  <div class="main-carousel">
   <div
      class="carousel-cell"
      :style="`background-image:url(${image})`"
      v-for="(image, index) in images"
      :key="index"
    ></div> 
    
  </div>
</template>
<style scoped>
.main-carousel {
  padding-top: 10px;
  width: 600px;
  height: 400px;

  border-radius: 5px;
  margin: 0 auto;
}
.carousel-cell {
  width: 600px;
  height: 400px;
  background-position: center;
  background-size: cover;
 
}
</style>

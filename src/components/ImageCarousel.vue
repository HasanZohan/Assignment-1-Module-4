<script setup>
import { ref } from 'vue';

const images = ref([
  // You can add your image URLs here dynamically.
  'https://cdn.pixabay.com/photo/2016/09/25/23/27/parachutist-1694886_1280.jpg',
  'https://randomwordgenerator.com/img/picture-generator/hourglass-1875812_640.jpg',
  'https://randomwordgenerator.com/img/picture-generator/54e9d4434855a514f1dc8460962e33791c3ad6e04e5074417d2d73d29f45c5_640.jpg',
  'https://randomwordgenerator.com/img/picture-generator/52e3d6434b5bb10ff3d8992cc12c30771037dbf85254784a742d7fd69e4f_640.jpg',
  'https://randomwordgenerator.com/img/picture-generator/54e5d2464f55a914f1dc8460962e33791c3ad6e04e50744077297bd5954ec6_640.jpg'
]);

const currentIndex = ref(0);

const prevSlide = () => {
  if (currentIndex.value > 0) {
    currentIndex.value--;
  }
};

const nextSlide = () => {
  if (currentIndex.value < images.value.length - 1) {
    currentIndex.value++;
  }
};
</script>

<template>
    <div class="carousel">
      <div class="carousel-container" :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
        <div v-for="(image, index) in images" :key="index" class="carousel-slide">
          <div class="card">
            <img :src="image" alt="Carousel Slide" class="card-img">
          </div>
        </div>
      </div>
    </div>
    <div class="carousel-navigation">
      <button @click="prevSlide" class="carousel-nav-btn">
        <i class="fas fa-chevron-left"></i>
        Prev
      </button>
      <button @click="nextSlide" class="carousel-nav-btn">
        Next
        <i class="fas fa-chevron-right"></i>
      </button>
    </div>
</template>
  
<style>
.carousel {
  position: relative;
  width: 100%;
  overflow: hidden;
}

.carousel-container {
  display: flex;
  transition: transform 0.3s ease;
}

.carousel-slide {
  flex: 0 0 100%;
}

.card {
  display: inline-block;
  border: 5px solid blue;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  box-sizing: border-box; /* Include border in width and height calculation */
}

.card-img {
  width: 600px;
  height: 400px;
  object-fit: cover;
  margin: 0; /* Remove the default margin on the img */
}

.carousel-navigation {
  display: flex;
  justify-content: center; /* Center align the buttons horizontally */
  margin-top: 10px;
}

.carousel-nav-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #000;
  color: #fff;
  font-size: 1rem;
  width: 100px; /* Adjust the width based on your design */
  height: 40px;
  border: none;
  border-radius: 5px;
  margin: 5px;
  cursor: pointer;
}

.carousel-nav-btn i {
  margin-right: 5px;
}
</style>

  
  



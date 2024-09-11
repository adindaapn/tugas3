<template>
  <div class="container">
    <!-- Click Counter -->
    <div class="counter">
      <p>Counter: {{ count }}</p>
      <button @click="increment">Tambah Counter</button>
    </div>

    <!-- Box Color Changer -->
    <div class="color-changer">
      <div :style="{ backgroundColor: boxColor }" class="box"></div>
      <button @click="changeColor">Ubah Warna Box</button>
    </div>

    <!-- Image Carousel -->
    <div class="image-carousel">
      <div class="carousel">
        <button @click="prevImage">Previous</button>
        <img :src="images[currentImageIndex]" alt="carousel image" />
        <button @click="nextImage">Next</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'; // Menggunakan reactive data

// Click Counter
const count = ref(0);
const increment = () => {
  count.value++;
};

// Box Color Changer
const boxColor = ref('lightgray');
const changeColor = () => {
  const colors = ['lightgray', 'pink', 'RoyalBlue', 'LightSalmon', 'LightSkyBlue',];
  boxColor.value = colors[Math.floor(Math.random() * colors.length)];
};

// Image Carousel
import image1 from '@/assets/Kucing.jpg';
import image2 from '@/assets/Kucing1.jpg';
import image3 from '@/assets/Kucing2.jpg';
import image4 from '@/assets/Kucing3.jpg';

const currentImageIndex = ref(0);
const images = [image1, image2, image3, image4];
const nextImage = () => {
  currentImageIndex.value = (currentImageIndex.value + 1) % images.length;
};
const prevImage = () => {
  currentImageIndex.value = (currentImageIndex.value - 1 + images.length) % images.length;
};
</script>

<style scoped>
body {
  font-family: Arial, sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  margin: 0;
  background-color: #f0f0f0;
}

.container {
  width: 80%;
  margin: 0 auto;
  text-align: center;
}

.box {
  width: 200px;
  height: 200px;
  margin: 20px auto;
  transition: background-color 0.3s ease;
}

.carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}

.carousel img {
  width: 300px;
  height: 300px;
  object-fit: cover;
  margin: 0 10px;
}

button {
  padding: 10px 20px;
  margin: 10px;
  cursor: pointer;
  font-size: 1rem;
}

.counter, .color-changer, .image-carousel {
  margin-bottom: 20px;
}
</style>

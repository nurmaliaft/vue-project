<template>
  <div id="app">
    <div class="container">
      <div class="section">
        <h2>Click Counter</h2>
        <p>Click count: {{ count }}</p>
        <button @click="increment">Increment</button>
        <button @click="reset">Reset</button>
      </div>

      <div class="section">
        <h2>Box Color Changer</h2>
        <div :style="{ backgroundColor: boxColor, width: '200px', height: '200px', margin: 'auto' }" class="color-box"></div>
        <button @click="Change">Change</button>
      </div>

      <div class="section">
        <h2>Image Carousel</h2>
        <div class="carousel">
          <img :src="images[currentImageIndex]" alt="Image Carousel" />
          <button @click="prevImage">Previous</button>
          <button @click="nextImage">Next</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import pic1 from '@/assets/pic1.jpeg';
import pic2 from '@/assets/pic2.jpeg';
import pic3 from '@/assets/pic3.jpeg';

export default {
  data() {
    return {
      count: 0,
      boxColor: 'brown',
      images: [pic1, pic2, pic3],
      currentImageIndex: 0
    };
  },
  methods: {
    increment() {
      this.count++;
    },
    reset() {
      this.count = 0;
    },
    Change() {
      const colors = ['Brown', 'Yellow', 'Green', 'Blue', 'Purple', 'Orange'];
      this.boxColor = colors[Math.floor(Math.random() * colors.length)];
    },
    prevImage() {
      this.currentImageIndex = (this.currentImageIndex - 1 + this.images.length) % this.images.length;
    },
    nextImage() {
      this.currentImageIndex = (this.currentImageIndex + 1) % this.images.length;
    }
  }
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: brown;
  margin-top: 20px;
}

.container {
  width: 80%;
  margin: 0 auto;
}

.section {
  margin: 20px 0;
}

.color-box {
  border: 1px solid #000;
  margin: 10px auto;
}

.carousel img {
  max-width: 100%;
  height: auto;
  display: block;
  margin: 0 auto;
}

button {
  margin: 5px;
  padding: 5px 5px;
  font-size: 14px;
  cursor: pointer;
  width: 35%;
}

</style>
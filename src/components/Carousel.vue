<template>
  <div class="carousel-container">
    <div class="carousel">
      <div v-for="(image, index) in images" :key="index" class="carousel-item" :class="{ 'active': index === activeIndex }">
        <img :src="image.url" :alt="image.alt" class="carousel-img"/>
        <div class="carousel-overlay">
          <h3 class="carousel-title">{{ image.title }}</h3>
          <p class="carousel-description">{{ image.description }}</p>
          <button class="carousel-button">View Details</button>
        </div>
      </div>
    </div>
    <button class="prev" @click="prevImage">&#10094;</button>
    <button class="next" @click="nextImage">&#10095;</button>
    <div class="carousel-indicators">
      <span v-for="(image, index) in images" :key="'indicator-' + index" :class="['indicator', { 'active': index === activeIndex }]" @click="scrollTo(index)"></span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Carousel',
  data() {
    return {
      images: [
        { url: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRkjLYn59rXIXBBjdOSwsTygv1KCzl8KKfeAw&s' },
        { url: 'https://images.puma.com/image/upload/q_auto,f_auto,w_1440/regional/%7Eregional%7ESEA%7Eothers%7EKOP%7E003+-+Landing+Pages%7E002-ss24%7EYear+Of+Sports%7E24SS_Ecom_YOS_BB_Lamelo-Ball_Full-Bleed-Hero_Large_Desk_1440x500px.jpg/fmt/jpg/fmt/png', alt: 'Image 2', title: 'Sepatu Basket MB.03 CLT', description: 'Rp 2.399.000' },
        { url: 'https://images.puma.com/image/upload/q_auto,f_auto,w_600/regional/%7Eregional%7EIDN%7Eothers%7EKOP%7EFull+Bleed+Hero%7EVelophasis+Bliss+-+SS24%7E24SS_ECOM_SP_Velophasis_DROP-2_Product_Full-Bleed-Hero_Large_Tab-Mob_1536x1536px.jpg/fmt/jpg/fmt/png', alt: 'PUMA x PLEASURES Velophasis Overdye', title: 'PUMA x PLEASURES Velophasis Overdye', description: 'Rp 2.499.000' }
      ],
      activeIndex: 0,
      interval: null
    };
  },
  methods: {
    scrollTo(index) {
      this.activeIndex = index;
      this.resetInterval();
    },
    prevImage() {
      this.activeIndex = (this.activeIndex - 1 + this.images.length) % this.images.length;
      this.resetInterval();
    },
    nextImage() {
      this.activeIndex = (this.activeIndex + 1) % this.images.length;
      this.resetInterval();
    },
    startAutoPlay() {
      this.interval = setInterval(this.nextImage, 3000);
    },
    resetInterval() {
      clearInterval(this.interval);
      this.startAutoPlay();
    }
  },
  mounted() {
    this.startAutoPlay();
  },
  beforeDestroy() {
    clearInterval(this.interval);
  }
}
</script>

<style scoped>
/* Carousel Container */
.carousel-container {
  position: relative;
  width: 100%;
  max-width: 1200px; /* Increase max-width to make the carousel larger */
  height: 600px; /* Increase height to make the carousel larger */
  margin: auto;
  overflow: hidden;
  border-radius: 16px;
}

/* Carousel Items */
.carousel-item {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: opacity 0.5s ease;
  border-radius: 16px;
  overflow: hidden;
}

/* Image Styling */
.carousel-img {
  width: 100%; /* Maintain width at 100% */
  height: 100%; /* Maintain height at 100% */
  object-fit: cover;
  border-radius: 16px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  border: 2px solid transparent;
  transition: transform 0.5s ease, box-shadow 0.3s ease, border-color 0.3s ease;
}

.carousel-item.active .carousel-img {
  transform: scale(1.05);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  border-color: #ffbf00;
}

.carousel-item .carousel-img:hover {
  transform: scale(1.03);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

/* Overlay Styling */
.carousel-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  padding: 20px;
  background: rgba(0, 0, 0, 0.7);
  transition: background 0.5s ease;
  border-radius: 0 0 16px 16px;
}

.carousel-overlay:hover {
  background: rgba(0, 0, 0, 0.9);
}

/* Text Styling */
.carousel-title {
  font-size: 24px;
  color: #fff;
  margin-bottom: 10px;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.75);
}

.carousel-description {
  font-size: 18px;
  color: #fff;
  margin-bottom: 20px;
}

/* Button Styling */
.carousel-button {
  padding: 12px 24px;
  background: linear-gradient(135deg, #ffbf00, #ff8000);
  color: #111;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.3s ease, transform 0.3s ease;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
}

.carousel-button:hover {
  background: linear-gradient(135deg, #111, #333);
  color: #ffbf00;
  transform: scale(1.1);
}

.carousel-item.active {
  opacity: 1;
}

/* Arrow Buttons */
.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 50%;
  width: auto;
  margin-top: -20px; /* Adjusted from -22px to -20px */
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  transition: 0.3s ease;
  user-select: none;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.7);
}

.prev:hover, .next:hover {
  background: rgba(0, 0, 0, 0.9);
}

.prev {
  left: 10px;
}

.next {
  right: 10px;
}

/* Indicators */
.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 8px;
}

.indicator {
  width: 12px;
  height: 12px;
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 50%;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.indicator.active {
  background-color: #ffbf00;
}

.indicator:hover {
  transform: scale(1.2);
}


.carousel-item.active {
  opacity: 1;
}

/* Arrow Buttons */
.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 50%;
  width: auto;
  margin-top: -20px; /* Adjusted from -22px to -20px */
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  transition: 0.3s ease;
  user-select: none;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.7);
}


.prev:hover, .next:hover {
  background: rgba(0, 0, 0, 0.9);
}

.prev {
  left: 10px;
}

.next {
  right: 10px;
}

/* Indicators */
.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 8px;
}

.indicator {
  width: 12px;
  height: 12px;
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 50%;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.indicator.active {
  background-color: #ffbf00;
}

.indicator:hover {
  transform: scale(1.2);
}
</style>

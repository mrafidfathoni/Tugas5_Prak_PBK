<template>
  <div class="card">
    <div class="image-container">
      <img :src="url" alt="Card image" class="card-image" />
    </div>
    <div class="card-content">
      <h2 class="cake-title">{{ title }}</h2>
      <p class="cake-price">{{ description }}</p>
      <button class="buy-button">Buy Now</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    url: {
      type: String,
      required: true,
    },
  },
};
</script>

<style>
.card {
  position: relative;
  border: none;
  border-radius: 16px;
  overflow: hidden;
  width: 320px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  background: linear-gradient(135deg, #333, #111);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.card:hover {
  transform: translateY(-10px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.3);
}

.image-container {
  width: 100%;
  height: 220px;
  overflow: hidden;
  border-bottom: 2px solid #ffbf00;
}

.card-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.card:hover .card-image {
  transform: scale(1.1);
}

.card-content {
  padding: 20px;
  background: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(10px);
  border-top: 2px solid #ffbf00;
}

.cake-title {
  font-family: "Arial", sans-serif;
  font-size: 26px;
  color: #fff;
  margin: 0 0 10px;
  transition: color 0.3s ease;
}

.card:hover .cake-title {
  color: #ffbf00;
}

.cake-price {
  font-family: "Courier New", Courier, monospace;
  font-size: 20px;
  color: #ffa500;
  margin: 0 0 20px;
}

.buy-button {
  display: block;
  width: 100%;
  padding: 12px 20px;
  font-family: "Arial", sans-serif;
  font-size: 16px;
  color: #fff;
  background: linear-gradient(135deg, #007bff, #0056b3);
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.3s ease, transform 0.3s ease;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
}

.buy-button:hover {
  background: linear-gradient(135deg, #0056b3, #004080);
  transform: translateY(-2px);
  box-shadow: 0 8px 12px rgba(0, 0, 0, 0.3);
}
</style>

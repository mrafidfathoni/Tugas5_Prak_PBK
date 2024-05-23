<template>
  <div>
    <Navbar />
    <div class="container mt-4">
      <Carousel />
      <div class="product-list mt-4">
        <Card
          v-for="product in products"
          :key="product.id"
          :title="product.name"
          :description="product.description"
          :url="product.image"
        />
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
import Carousel from './components/Carousel.vue';
import Card from './components/Card.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components: {
    Navbar,
    Carousel,
    Card,
    Footer
  },
  data() {
    return {
      products: [
        { id: 1, name: 'Amare Fresh Running Shoes', description: 'Dari Rp 989.100 -42%', image: 'https://www.static-src.com/wcsstore/Indraprastha/images/catalog/full/catalog-image/MTA-117454638/puma_puma_unisex_running_shoes_amare_fresh_sepatu_lari_-37875106-_full02_b59wev7g.jpeg' },
        { id: 2, name: 'Puma ACTIVE Mens Jacket - Black', description: 'Rp. 639.000', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQh5-EgRpFx7d9bMMW2MR-v8X9vRsmFB3sXsg&s' },
        { id: 3, name: 'rs-x "40th anniversary" unisex sneakers shoes - vapor gray', description: 'Rp. 1.359.200', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTKYixzdxMxYqnJ7gbg5s9_jIr0lkj8zl3mIQ&s' },
        { id: 4, name: 'Kaus Pria Logo Active Small', description: 'Rp 499.000', image: 'data:image/jpeg;base64,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' },
        { id: 5, name: 'Puma Set pria ritsleting Hoodie + celana', description: 'Rp276.867', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTgcb3HOgaBmLQjmPJOke1jJT9Xqu07N9kvkw&s' },
        { id: 6, name: 'PUMA x PLAYSTATION', description: 'Rp1.599.000', image: 'https://cdn.gamerwk.com/2024/04/%E3%83%A1%E3%83%B3%E3%82%BA-PUMA-x-PlayStation-%E3%82%B0%E3%83%A9%E3%83%95%E3%82%A3%E3%83%83%E3%82%AF-%E3%83%95%E3%83%BC%E3%83%87%E3%82%A32.png' },
        { id: 7, name: 'PUMA Sepatu Club Zone Sneakers White', description: 'Rp 659.400', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTtKP3vhFGiY-M-fQI8tbERgRP6wA4ZNi1hfA&s' },
        { id: 8, name: 'Kaos Jersey Youth AC Milan 23/24 ', description: 'Rp 699.300', image: 'data:image/jpeg;base64,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' },
        { id: 9, name: 'Puma Ultra Match FG/AG 107217 02 - Black/White', description: 'Rp875.000', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSCrx6vLLpdznWGxwPaUbdz42ezVN_XgLrwng&s' },
        { id: 10, name: 'Puma Suede One Piece Straw Hat Luffy', description: 'Rp1.599.000', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ8CXeTaXwxyrQ9evY9CqghP7xZzXrRZsZosg&s' },
        { id: 11, name: 'Puma X NCT 127 Slipstream Low INVDR', description: 'Rp479.700 70%', image: 'https://images.jdsports.id/i/jpl/jd_38854901_a?w=700&resmode=sharp&qlt=70&fmt=webp' },
        { id: 12, name: 'Puma ftblPLAY TRACKSUIT JR', description: 'Rp300.000', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSVEvsivxXwed4A36wHmsbp7x3VEM_TTBlX5H94F-4f_jG5AOTIrvscWoSGe_qiyjdF9dQ&usqp=CAU' }
      ]
    };
  }
};
</script>

<style>
body {
  background-color: #f5f5f5;
  font-family: 'Arial', sans-serif;
  margin: 0;
  padding: 0;
  color: #333;
}

.container {
  max-width: 1200px;
  margin: 10px auto;
  padding: 0 15px;
}

.mt-4 {
  margin-top: 2rem;
}

.product-list {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}

.card {
  border: none;
  border-radius: 16px;
  overflow: hidden;
  width: calc(25% - 20px); /* 4 cards per row */
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  background: linear-gradient(135deg, #333, #111);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: scale(1.05);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.3);
}

.image-container {
  width: 100%;
  height: 220px;
  overflow: hidden;
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
  background: rgba(0, 0, 0, 0.7);
  backdrop-filter: blur(10px);
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
}

.buy-button:hover {
  background: linear-gradient(135deg, #0056b3, #004080);
  transform: translateY(-2px);
}

@media (max-width: 1024px) {
  .card {
    width: calc(33.333% - 20px); /* 3 cards per row for tablets and smaller screens */
  }
}

@media (max-width: 768px) {
  .card {
    width: calc(50% - 20px); /* 2 cards per row for smaller tablets */
  }
}

@media (max-width: 480px) {
  .card {
    width: 100%; /* 1 card per row for mobile devices */
  }
}
</style>

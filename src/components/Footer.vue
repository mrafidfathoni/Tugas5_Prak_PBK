<template>
  <footer class="footer">
    <div class="footer-wave">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320"><path fill="#111" fill-opacity="1" d="M0,64L80,74.7C160,85,320,107,480,117.3C640,128,800,128,960,122.7C1120,117,1280,107,1360,101.3L1440,96L1440,320L1360,320C1280,320,1120,320,960,320C800,320,640,320,480,320C320,320,160,320,80,320L0,320Z"></path></svg>
    </div>
    <div class="footer-content">
      <div class="social-icons">
        <a href="#" class="social-icon"><i class="fab fa-facebook-f"></i></a>
        <a href="#" class="social-icon"><i class="fab fa-twitter"></i></a>
        <a href="#" class="social-icon"><i class="fab fa-instagram"></i></a>
      </div>
      <p>&copy; 2024 PumaZing. All rights reserved.</p>
      <p>Contact us: contact@pumazing.com</p>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style>
.footer {
  position: relative;
  background: linear-gradient(135deg, #111, #222, #111);
  color: #fff;
  text-align: center;
  padding: 60px 0;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
  z-index: 2;
}

.social-icons {
  margin-bottom: 30px;
}

.social-icon {
  color: #fff;
  font-size: 26px;
  margin-right: 15px;
  transition: color 0.3s ease, transform 0.3s ease, text-shadow 0.3s ease;
}

.social-icon:hover {
  color: #ffbf00;
  transform: scale(1.3);
  text-shadow: 0 0 10px rgba(255, 191, 0, 0.8);
}

.footer p {
  font-size: 18px;
  margin: 10px 0;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
}

.footer-wave {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  overflow: hidden;
  line-height: 0;
  transform: rotate(180deg);
  z-index: 1;
}

.footer-wave svg {
  position: relative;
  display: block;
  width: calc(100% + 1.3px);
  height: 100px;
}
</style>

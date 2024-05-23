<template>
  <nav class="navbar">
    <div class="logo">PumaZing</div>
    <ul class="nav-links">
      <li><a href="#home">Home</a></li>
      <li><a href="#products">Products</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>
</template>

<style>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: linear-gradient(135deg, #050505, #7c7f82);
  padding: 15px 20px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: background-color 0.3s ease, box-shadow 0.3s ease;
  border-radius: 10px; /* Rounded corners */
}

.logo {
  color: #fff;
  font-size: 28px;
  font-weight: bold;
  cursor: pointer;
  background: linear-gradient(135deg, #ffbf00, #ff6600);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  transition: transform 0.3s ease, background 0.3s ease;
}

.logo:hover {
  transform: scale(1.1);
  background: linear-gradient(135deg, #ff6600, #ffbf00);
}

.nav-links {
  list-style: none;
  display: flex;
}

.nav-links li {
  margin: 0 15px;
}

.nav-links a {
  color: #fff;
  text-decoration: none;
  font-size: 18px;
  font-weight: 500;
  position: relative;
  transition: color 0.3s ease, transform 0.3s ease;
}

.nav-links a::before {
  content: '';
  position: absolute;
  width: 0%;
  height: 2px;
  bottom: -5px;
  left: 0;
  background-color: #ffbf00;
  transition: width 0.3s ease, background-color 0.3s ease;
}

.nav-links a:hover {
  color: #ffbf00;
  transform: translateY(-2px);
}

.nav-links a:hover::before {
  width: 100%;
}

.nav-links a::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 5px;
  transform: scale(0);
  transition: transform 0.3s ease;
  z-index: -1;
}

.nav-links a:hover::after {
  transform: scale(1.2);
}

.navbar {
  /* Gradient Background */
  background: linear-gradient(135deg, #050505, #7c7f82);
  /* Add padding and border radius for a more rounded look */
  padding: 15px 20px;
  border-radius: 10px; 
  /* Add box shadow for depth */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  /* Transition effects for smoother hover */
  transition: background-color 0.3s ease, box-shadow 0.3s ease;
}

.logo {
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5), 0 0 5px rgba(255, 255, 255, 1.5); 
}

.logo:hover {
  text-shadow: 2px 2px 4px rgba(1, 1, 1, 1.5); 
}

.nav-links a {
  /* Text Shadow */
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

.nav-links a:hover {
  /* Color change on hover */
  color: #ffbf00; 
  /* Move text slightly up on hover */
  transform: translateY(-2px); 
}
</style>

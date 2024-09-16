<template>
    <nav class="navbar">
      <div class="logo">
        <img src="@/assets/logo.png" alt="Logo" />
      </div>
      <ul class="nav-links">
        <li><router-link to="/">Home</router-link></li>
        <li>
          <div @mouseover="showDropdownAbout = true" @mouseleave="showDropdownAbout = false">
            About
            <ul v-if="showDropdownAbout">
              <li><router-link to="/about1">About Us</router-link></li>
              <li><router-link to="/team">Our Team</router-link></li>
              <li><router-link to="/story">Our Story</router-link></li>
            </ul>
          </div>
        </li>
        <li>
          <div @mouseover="showDropdownServices = true" @mouseleave="showDropdownServices = false">
            Services
            <ul v-if="showDropdownServices">
              <li><router-link to="/service1">Service 1</router-link></li>
              <li><router-link to="/service2">Service 2</router-link></li>
              <li><router-link to="/service3">Service 3</router-link></li>
            </ul>
          </div>
        </li>
        <li><router-link to="/contact">Contact</router-link></li>
      </ul>
      <button class="cta-button">Get Started</button>
    </nav>
  </template>
  
  <script>
  export default {
    data() {
      return {
        showDropdownAbout: false,
        showDropdownServices: false,
      };
    },
  };
  </script>
  
  <style scoped>
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #333;
    padding: 10px 20px;
    position: absolute;
    width: 100%;
    top: 0;
    z-index: 1;
  }
  
  .logo img {
    width: 100px;
  }
  
  .nav-links {
    list-style: none;
    display: flex;
    align-items: center;
  }
  
  .nav-links li {
    margin-right: 20px;
    position: relative;
  }
  
  .nav-links a {
    color: white;
    text-decoration: none;
  }
  
  ul li ul {
    position: absolute;
    top: 30px;
    left: 0;
    background-color: #444;
    list-style: none;
    padding: 10px;
    display: none;
  }
  
  ul li:hover ul {
    display: block;
  }
  
  .cta-button {
    background-color: #ff6b6b;
    color: white;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
    border-radius: 5px;
  }
  </style>
  
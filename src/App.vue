<template>
  <div id="app">
    <div class="header">
      <a href="#default" class="logo"><img style="width:50px;height:50px;" src="./assets/images/logo_footer.png" class="img_top" alt=""></a>
      <a>Daily Drinks</a>
      <div class="header-right">
        
        <a class="active" href="#home">Home</a>
        <a href="#contact">Contact</a>
        <a href="#about">About</a>
      </div>
    </div>
    <AddProduct />
    <Products />
  </div>
</template>

<script>
import Products from "./components/Products.vue";
import AddProduct from "./components/AddProduct.vue";

export default {
  name: "app",
  components: {
    Products,
    AddProduct
  }
};
</script>

<style>
*,
body {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
body {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background: #2c3e50;
  padding-top: 30px;
}
.header {
  overflow: hidden;
  background-color: #fff;
  padding: 20px 10px;
}
.header a {
  float: left;
  color: black;
  text-align: center;
  padding: 12px;
  text-decoration: none;
  font-size: 18px; 
  line-height: 25px;
  border-radius: 4px;
}

.header a.logo {
  font-size: 25px;
  font-weight: bold;
  margin-top:-13px;
}



.header a.active {
  background-color: dodgerblue;
  color: white;
}

.header-right {
  float: right;
}

  
  .header-right {
    float: none;
  }
#app {
  max-width: 700px;
  margin: 0 auto;
}
</style>

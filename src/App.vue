<template>
  <div id="app">
    <div class="header">
      <a href="#default" class="logo"><img style="width:50px;height:50px;" src="./assets/images/logo_footer.png" class="img_top" alt=""></a>
      <a class="title_anchor">Daily Drinks</a>
      <div class="header-right">
        
        <a class="active" href="#home">Home</a>
        <a href="#contact">Contact</a>
        <a href="#about">About</a>
      </div>
    </div>
    <AddProduct :product="formData" :index="currentProduct" />
    <Products :products="products" @edit="onEdit" />
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
  },
   data() {
    return {
      currentOrder: null,
        formData: {},
    }
  },

  // Data:{
  //   formData: {},
  //   currentOrder: null
  // },
  methods:{
     onEdit(index,allProducts) {
      // alert(allProducts[index])
      this.formData = allProducts[index];
      this.currentProduct = index;
      
    },
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
  background: #fff;
  /*padding-top: 30px;*/
}
.header {
  overflow: hidden;
  background-color: #fff;
  padding: 20px 10px;
      width: 1200px;
    margin: 0 auto;
}
.header a {
    float: left;
    color: black;
    text-align: center;
    padding: 8px;
    text-decoration: none;
    font-size: 16px;
    line-height: 25px;
    border-radius: 0px;
    padding-left: 25px;
    padding-right: 25px;
    font-weight: bold;
    font-family: sans-serif;
}

.header a.logo {
  font-size: 25px;
  font-weight: bold;
  margin-top:-13px;
}



.header a.active {
  background-color: #661f09;
  color: white;
}

.header-right {
     float: right;
    margin-right: 35px;
}
a.title_anchor {
    padding-left: 0;
    font-weight: bold;
    font-family: sans-serif;
    font-size: 22px;
    margin-left: -10px;
}

  
  
#app {
  max-width: 100%;
  margin: 0 auto;
}

@media(max-width: 767px)
{
  .header
  {
 width: 100%;
  }
}
</style>

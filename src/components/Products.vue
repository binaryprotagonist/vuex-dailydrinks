<template>
  <ul class="products-listing">
    <li v-for="(product,index) in allProducts" :key="product.name" :product="product"
      @edit="$emit('edit', index)">
      <img src="../assets/images/5.jpg" class="img_top" alt="" style="height:100px;width:100px;">
     <!-- <h3> {{ product.name }} | {{ product.price }} |{{product.description}}</h3> -->
    <p> <h3>Product Name</h3>:<span>{{product.name}}</span>
     <h3>Price</h3>:<span>{{product.name}}</span><br>
     <h3>Description</h3>:<span>{{product.name}}</span>
     <button @click="$emit('edit',index,allProducts)">
          <img src="https://image.flaticon.com/icons/svg/1250/1250615.svg" width="15" alt>
        </button>
      <button @click="deleteProduct(index)">Delete</button>
            
    </li>
  </ul>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "Products",
  filters: {
    currency: function(value) {
      return "₹ " + parseFloat(value).toFixed(2);
    }
  },
  methods: {
    ...mapActions(["getProducts", "deleteProduct"])
  },
  computed: mapGetters(["allProducts"]),
  created() {
    this.getProducts();
  }
  
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.products-listing li {
  background: #fff;
  padding: 15px;
  border-radius: 5px;
  margin-bottom: 20px;
  list-style: none;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.products-listing li button {
  background: #fff;
  border: 1px solid #fff;
  border-radius: 5px;
  color: #000;
  font-size: 16px;
  cursor: pointer;
}
</style>

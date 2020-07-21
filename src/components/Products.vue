<template>
  <div class="container">
  <ul class="products-listing">
    <li v-for="(product,index) in allProducts" :key="product.name" :product="product"
      @edit="$emit('edit', index)">
      
      <img src="../assets/images/5.jpg" class="img_top" alt="" style="height:auto;width:60%;">
     <!-- <h3> {{ product.name }} | {{ product.price }} |{{product.description}}</h3> -->





    <div class="col-custom"> <p> <h3><span>{{product.name}}</span></h3></div>
    <div class="col-custom"><span> $ {{product.price}}</span><br>   </div>
    <div class="col-custom"><span class="span_para">{{product.description}}</span>   </div>
     <button @click="$emit('edit',index,allProducts)" class="edit_btn">
          <!-- <img src="https://image.flaticon.com/icons/svg/1250/1250615.svg" width="15" alt> -->
          Edit
        </button>
      <button @click="deleteProduct(index)" class="delete_btn">Delete</button>
            
    </li>
  </ul>
</div>
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
    /*border-radius: 5px;*/
    margin-bottom: 20px;
    list-style: none;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    -webkit-box-pack: justify;
    -ms-flex-pack: justify;
    justify-content: space-between;
    width: 32%;
    display: inline-block;
    margin-right: 15px;
        box-shadow: 0px 1px 10px rgba(0,0,0,0.3);
}
.products-listing li button {
  background: #fff;
  border: 1px solid #fff;
  border-radius: 5px;
  color: #000;
  font-size: 16px;
  cursor: pointer;
}
.container {
    width: 1200px;
    margin: 0 auto;
}
button.edit_btn {
    width: 90px;
    background: #661f09 !important;
    height: 40px;
    font-family: sans-serif;
    font-weight: bolder;
    color: #fff !important;
    border-radius: 40px !important;
    margin-top: 10px;
    margin-right: 15px;
    border-radius: 0px;
}

button.delete_btn {
    width: 90px;
    background: #661f09 !important;
    height: 40px;
    font-family: sans-serif;
    font-weight: bolder;
    color: #fff !important;
    border-radius: 40px !important;
    margin-top: 10px;
    margin-right: 0px;
    border-radius: 40px;
        margin-bottom: 15px;
}
.col-custom h3 {
    text-align: center;
    font-size: 24px;
    padding-top: 10px;
    padding-bottom: 5px;
    font-family: sans-serif;
}
span.span_para {
    color: #767676;
    font-size: 18px;
    font-family: inherit;
}

@media(max-width: 767px)
{
  .container
  {
   width: 100%;
  }
  .products-listing li
  {
    width: 100%;
    display: block;
   
  }
}
</style>

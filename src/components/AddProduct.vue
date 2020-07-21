<template>
  <div class="add-product">
    <h2 v-if="product.name">Edit Order</h2>
      <h2 v-else>New Order</h2>
    <form @submit.prevent="onSubmit">
      <input type="text" v-model="name" placeholder="Add Product..." />
      <input type="text" v-model="price" placeholder="Add Price..." />
      <input type="text" v-model="description" placeholder="Add Description..." />
      <input type="submit" value="Submit" />
    </form>
  </div>

</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "AddProduct",
   props: {
    product: {
      type: Object,
      default: () => {
        return { name: '', price:'', notes:'' };
      }
      
    },index:{
      type: Number,
      default: null
    }
   },
  watch:{
    product(newVal){
      if(newVal.name){
        alert(newVal)
        this.name = newVal.name
        this.price = newVal.price
        this.description = newVal.description
      }
    }
  },
  data() {
    return {
      name: "",
      price: "",
      description:""
    };
  },
  methods: {
    ...mapActions(["addProduct"]),
    onSubmit() {
      
      this.addProduct({
        name: this.name,
        price: this.price,
        description:this.description,
        index:this.index
      });
      this.reset()
    },
    reset(){
      this.name = ''
      this.price = ''
      this.description = '',
      this.index=null,
      this.product={}
    }
  },
  
};
</script>

<style scoped>
.add-product {
  background: #fff;
  padding: 15px;
  margin-bottom: 20px;
      width: 1200px;
    margin: 0 auto;
/*    background: red;
*/    margin-top: 20px;
    margin-bottom: 22px;
}
form {
  display: flex;
  justify-content: space-between;
}
input[type="text"] {
     width: 270px;
    padding: 10px;
    border: 1px solid #171919;
    outline: 0;
    border-radius: 32px;
    padding-left: 17px;
}
.add-product h2 {
    margin-top: -15px;
    margin-bottom: 26px;
    font-family: sans-serif;
    font-size: 35px;
}
input[type="submit"] {
     width: 180px;
    background: #661f09;
    color: #fff;
    border: 1px #65251b solid;
    cursor: pointer;
    height: 45px;
    border-radius: 34px;
    font-weight: bold;
    font-family: sans-serif;
}

@media(max-width: 767px)
{
  form
  {
    display: block;
  }
  .add-product
  {
    width: 100%;
  }
  input[type="text"]

{
  margin-bottom: 20px;
}
}


</style>

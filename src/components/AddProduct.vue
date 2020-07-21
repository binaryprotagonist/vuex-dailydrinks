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
  border-radius: 5px;
  margin-bottom: 20px;
}
form {
  display: flex;
  justify-content: space-between;
}
input[type="text"] {
  width: 270px;
  padding: 10px;
  border: 1px solid #2c3e50;
  outline: 0;
}
input[type="submit"] {
  width: 120px;
  background: #2c3e50;
  color: #fff;
  border: 1px #2c3e50 solid;
  cursor: pointer;
}
</style>

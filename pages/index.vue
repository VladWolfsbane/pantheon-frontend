<template>
  <div class="home">
    <div class="categories">
      <Categories :categories="categories"/>
    </div>
    <div class="main">

        <img class="bannerImage" src="/banner.png"/>
    </div>

    <div>
        <h1 class="head" style="background-color: rgb(97, 0, 0); color: white;">R E C O M M E N D A T I O N S</h1>
        <hr>
        <div class="products">
          <div style="text-align:center;" class="product" v-for="item in products.slice(0, 4)" :key="item._id">
            <Product :product-id="item._id" :product-title="item.title"
            :product-price="item.price" :product-rating="item.rating"
            :product-photo="item.photo" :productDetailsButton="false"
          />
        </div>
    </div>
    <hr>

  </div>
  <h1 class="head" style="background-color: rgb(97, 0, 0); color: white;">C A T E G O R I E S</h1>
  <div style="text-align:center">
      <div class="bottom-banner">
    <a href="/category/60a17c664e266c098c793ff7" style="color:grey; text-decoration: none"><div class="card" style="width: 18rem;">
  <img class="card-img-top" src="/mens-fashion.jpg" alt="Image Broken">
  <div class="card-body">
    <h5 class="card-title">Mens Fashion</h5>
    <p class="card-text">Your Destination For Style Discovery and Inspiration - Free Shipping and Free Returns. Curate Your Closet With The Season's Must-Have Clothing, Shoes and Accessories. Shop Online.</p>
  </div>
</div></a>

      <a href="/category/60a17ce84e266c098c793ff8" style="color:grey; text-decoration: none"><div class="card" style="width: 18rem;">
  <img class="card-img-top" src="/womens-fashion.jpg" alt="Image Broken">
  <div class="card-body">
    <h5 class="card-title">Womens Fashion</h5>
    <p class="card-text">Find us Online or come to the Physical Shop in downtown. Moto and Rock Style. Nahast Meeste Saapad. Boots and Shoes. Dress and Casual shoes.</p>
  </div>
</div></a>

      <a href="/category/60a17d494e266c098c793ff9" style="color:grey; text-decoration: none"><div class="card" style="width: 18rem;">
  <img class="card-img-top" src="/accessories.jpg" alt="Image Broken">
  <div class="card-body">
    <h5 class="card-title">Accessories</h5>
    <p class="card-text">Accessories are the best way to update your look – add a little edge with new styles and colors. Find everything in our women's accessories department.</p>
  </div>
</div></a>

      <a href="/category/60a17d7e4e266c098c793ffa" style="color:grey; text-decoration: none"><div class="card" style="width: 18rem;">
  <img class="card-img-top" src="/travel-equipments.jpg" alt="Card image cap">
  <div class="card-body">
    <h5 class="card-title">Travel Equipments</h5>
    <p class="card-text">From leak-proof bottles to wireless noise-cancelling headphones, these are the best travel accessories to solve all your problems on the go.</p>
  </div>
</div></a><br><br><br><br><br>
</div>

  </div>
  <h5 style="margin-top:5rem;background-color:rgb(97, 0, 0);color:white;text-align:center;padding:1rem;">Copyright 2021 | All Rights Reserved</h5>
  </div>
</template>

<script>
import Product from '../components/Product';
import Categories from '../components/Categories';
export default {
  name: 'Home',
  components: {
    Product,
    Categories
  },

  async asyncData({$axios}){
    try{
      let response = await $axios.$get("http://localhost:5000/product/getAllProducts");
      let response2 = await $axios.$get("http://localhost:5000/category/getCategories");
      return {
        products: response.products,
        categories: response2.categories,
      }
    }catch(err){
      console.log(err);
    }
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


.home{
  margin-bottom: 100px;
}

.search{
  display: flex;
  justify-content: center;
  padding: 10px;
}

.categorySection{
  background-color: rgb(97, 0, 0);
}

.navbar-expand-lg{
  background-color: rgb(97, 0, 0);
}

.bannerImage{
  object-fit: contain;
  width: 100%;
}

.head {
  text-align: center;
  margin-top: 30px;
}

.products{
  display: flex;
  justify-content: space-around;
  margin: 30px;
}

.bottom-banner{
  display: flex;
  justify-content: space-around;
  margin-top: 80px;
}

.bottom-banner-child{
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  margin-bottom: 50px;
}

.card{
  transition: transform 450ms;
}
.card:hover {
  transform: scale(1.06);
  box-shadow: 0 0 10px #515151;
  cursor: pointer;
}

.card-img-top{
  object-fit: contain;
  height: 300px;
}

</style>

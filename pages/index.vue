<template>
<div style="font-family: Times New Roman, Times, serif;">
	<div class="home"></div>
	<div class="categories">
		<Categories :categories="categories"/>
	</div>
	<div class="main">
		<img class="bannerImage" src="/141_20201013185512_Consumer Survey Finds 70 Percent of Travelers Plan to Holiday in 2021.jpg"/>
	</div>
	<div>
		<h1 class="head">About</h1>
    <p style="text-align: center">Best place to shop all your travel necessities for the best price. Deliveries within 1 week. Lorem ipsum dolor sit amet consectetur adipisicing elit. Ratione at neque illum a libero nulla autem vitae, dolor alias ut omnis repudiandae saepe nam possimus sunt optio ipsam dolore veniam? Lorem ipsum dolor, sit amet consectetur adipisicing elit. Laboriosam veniam pariatur molestiae amet, et quas sed modi eaque illum quae enim adipisci nisi eligendi repudiandae, hic esse praesentium nostrum neque! Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptate qui mollitia quod blanditiis maiores! Ipsa enim, ab tenetur illum numquam eveniet nesciunt unde, odit excepturi quibusdam laboriosam nam consectetur quis.</p>
		<hr>
			<div class="products">
				<div class="product" v-for="item in products.slice(0, 4)" :key="item._id">
					<Product :product-id="item._id" :product-title="item.title"
            :product-price="item.price" :product-rating="item.rating"
            :product-photo="item.photo" :productDetailsButton="false"
          />
				</div>
			</div>
			<hr>
				<img class="bannerImage" src="travel-experience-1x.jpg"/>
			</div>
			<div class="bottom-banner">
				<div class="card" style="width: 18rem;">
					<img class="card-img-top" src="https://www.creditwalk.ca/wp-content/uploads/2017/11/Linda-electronics-1-e1510481621452.jpg" alt="Card image cap">
						<div class="card-body">
							<h5 class="card-title">Electronics</h5>
							<NuxtLink class="btn btn-dark" to="/category/60a6cd404a7cbe4563ad4f73">Shop Now</NuxtLink>
						</div>
					</div>
					<div class="card" style="width: 18rem;">
						<img class="card-img-top" src="https://www.savethestudent.org/uploads/colourful-clothes-on-a-rail.jpg" alt="Card image cap">
							<div class="card-body">
								<h5 class="card-title">Clothes</h5>
								<NuxtLink class="btn btn-dark" to="/category/60a6cd474a7cbe4563ad4f74">Shop Now</NuxtLink>
							</div>
						</div>
						<div class="card" style="width: 18rem;">
							<img class="card-img-top" src="https://pyxis.nymag.com/v1/imgs/083/cf6/c42515e515bbb88e06e86a9d327cf73516-amazon-luggage-lede.2x.rhorizontal.w700.jpg" alt="Card image cap">
								<div class="card-body">
									<h5 class="card-title">Luggage</h5>
									<NuxtLink class="btn btn-dark" to="/category/60a6cd524a7cbe4563ad4f75">Shop Now</NuxtLink>
								</div>
							</div>
							<div class="card" style="width: 18rem;">
								<img class="card-img-top" src="https://trace-elliot.co.uk/temedia/2019/04/blog-TE.jpg" alt="Card image cap">
									<div class="card-body">
										<h5 class="card-title">Miscellaneous</h5>
										<NuxtLink class="btn btn-dark" to="/category/60a6cd184a7cbe4563ad4f72">Shop Now</NuxtLink>
									</div>
								</div>
							</div>
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

.btn {
  background-color: red;
  border: none,
}

.bottom-banner{
  display: flex;
  justify-content: space-around;
  margin-top: 80px;
  color: blue;
}

.bottom-banner-child{
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  margin-bottom: 50px;
  color: blue;
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
<template>
  <div class="hero">
    <div id="search-bar">
      <div class="search-tool">
        <h3>Enter Region:</h3>
        <input type="text" v-model="region" placeholder="Region/Location" />
      </div>
      <div class="search-tool">
        <h3>Sort By:</h3>
        <select v-model="sortBy">
          <option value="type">Type</option>
          <option value="category">Category</option>
          <!-- <option value="price">Price</option> -->
          <option value="region">Location</option>
          <!-- <option value="area">Size</option> -->
          <!-- <option value="category">Category</option> -->
        </select>
      </div>
      <div class="search-tool">
        <h3>Price Range:</h3>
        <label for="vol">400 to 5000</label>
        <input type="range" v-model="price" min="400" max="5000" step="10" />
        {{ price }}
      </div>
      <div class="search-tool">
        <h3>Property Type:</h3>
        Villa: <input type="checkbox" value="Villa" v-model="types" /> Room:
        <input type="checkbox" value="Room" v-model="types" /> Appartment:
        <input type="checkbox" value="Appartment" v-model="types" /> Chalet:
        <input type="checkbox" value="Chalet" v-model="types" /> House:
        <input type="checkbox" value="House" v-model="types" /> Land:
        <input type="checkbox" value="Land" v-model="types" />
      </div>
      <div class="search-tool">
        <h3>Filter By Category:</h3>
        Rent: <input type="checkbox" value="Rent" v-model="categories" /> Buy:
        <input type="checkbox" value="Buy" v-model="categories" />
      </div>
    </div>

    <div v-if="filterProducts.length != 0" class="box pt-b" id="products-grid">
      <div
        class="product-box"
        v-for="(product, index) in filterProducts"
        :class="index % 2 == 0 ? 'bg-light' : 'bg-dark'"
        :key="index"
      >
        Property Region: <strong>{{ product.region }}</strong> - Product Type:
        <strong>{{ product.type }}</strong> - Product Price:
        <strong>{{ product.price }}</strong> - Product Category:
        <strong>{{ product.category }}</strong> - Product Area:
        <strong>{{ product.area }}</strong>
        <div id="product-image">
          <img src="http://via.placeholder.com/350x250" alt="property image" />
        </div>
      </div>
    </div>
    <div v-else class="pt-b" id="box">
      <div class="product-box">
        <p>
          No Match Found!!!
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Gallery",
  data() {
    return {
      categories: [],
      types: [],
      prices: [],
      price: 5000,
      region: "",
      sortBy: "type",
      // category: "",
      products: [
        {
          region: "Beirut",
          type: "Appartment",
          price: "1000",
          category: "Rent",
          area: 253
        },
        {
          region: "Jbeil",
          type: "Room",
          price: "400",
          category: "Rent",
          area: 35
        },
        {
          region: "Jal el dib",
          type: "Chalet",
          price: "1500",
          category: "Rent",
          area: 75
        },
        {
          region: "Jbeil",
          type: "Villa",
          price: "600",
          category: "Buy",
          area: 750
        },
        {
          region: "Jounieh",
          type: "Appartment",
          price: "899",
          category: "Buy",
          area: 300
        },
        {
          region: "Beirut",
          type: "House",
          price: "1500",
          category: "Rent",
          area: 500
        },
        {
          region: "Tripoli",
          type: "Chalet",
          price: "2",
          category: "Rent",
          area: 300
        },
        {
          region: "Dbayeh",
          type: "Villa",
          price: "1500",
          category: "Buy",
          area: 1000
        },
        {
          region: "Rabieh",
          type: "Appartment",
          price: "2500",
          category: "Rent",
          area: 150
        },
        {
          region: "Kfardebian",
          type: "Land",
          price: "4000",
          category: "Buy",
          area: 2000
        }
      ]
    };
  },
  computed: {
    filterProducts: function() {
      return this.products
        .filter(item => {
          return (
            (this.region.length === 0 || item.region.includes(this.region)) &&
            (this.categories.length === 0 ||
              this.categories.includes(item.category)) &&
            (this.types.length === 0 || this.types.includes(item.type)) &&
            (this.price.length === 0 ||
              (item.price > 0 && item.price < this.price))
          );
        })
        .sort((a, b) => {
          return a[this.sortBy]
            .toString()
            .localeCompare(b[this.sortBy].toString());
        });
    }
  }
};
</script>

<style lang="scss" scoped>
#type {
  display: flex;
  flex-wrap: flex-wrap;
}
#search-bar {
  margin-right: auto;
  margin-left: auto;
  flex-wrap: wrap;
  justify-content: center;
  display: flex;
}
.search-tool {
  width: 400px;
  margin-right: 1rem;
  margin-left: 1rem;
}
#products-grid {
  // display: flex;
  // flex-wrap: wrap;
  // justify-content: center;
  // align-content: center;
  // background-color: whitesmoke;

  // height: 100%;
  // overflow-y: scroll;
}
.hero {
  width: 100%;
  height: 100vh;
  // overflow: hidden;
}
.product-box {
  margin-right: auto;
  margin-left: auto;
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
  // padding-top: 1rem;
  // padding-bottom: 1rem;
  width: 350px;
  height: 400px;
}
.pt-b {
  margin-top: 3rem;
  margin-bottom: 3rem;
  padding-top: 1.5rem;
  padding-bottom: 1.5rem;
  margin-right: 0 !important;
  margin-left: 0 !important;
  padding-right: 0 !important;
  padding-left: 0 !important;
}
#box {
  width: 100%;
  min-height: 400px;
}
.bg-light {
  background-color: whitesmoke;
}
.bg-dark {
  background-color: grey;
}
</style>

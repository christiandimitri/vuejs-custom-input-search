<template>
  <div class="hero">
    <div id="search-box">
      <div class="is-search-tool">
        <h3>Enter Region:</h3>
        <input type="text" v-model="region" placeholder="Region/Location" />
      </div>
      <div class="is-search-tool">
        <h3>Property Type:</h3>
        Villa: <input type="checkbox" value="Villa" v-model="types" /> Room:
        <input type="checkbox" value="Room" v-model="types" /> Appartment:
        <input type="checkbox" value="Appartment" v-model="types" /> Chalet:
        <input type="checkbox" value="Chalet" v-model="types" /> House:
        <input type="checkbox" value="House" v-model="types" /> Land:
        <input type="checkbox" value="Land" v-model="types" />
      </div>
      <div class="is-search-tool">
        <h3>Filter By Category:</h3>
        Rent: <input type="checkbox" value="Rent" v-model="categories" /> Buy:
        <input type="checkbox" value="Buy" v-model="categories" />
      </div>
    </div>

    <ul id="products-grid">
      <li
        class="product-box"
        v-for="(product, index) in filterProducts"
        :key="index"
      >
        <div
          style="width: 100%; height:100%"
          :class="index % 2 == 0 ? 'bg-light' : 'bg-dark'"
        >
          Property Region: <strong>{{ product.region }}</strong> - Product Type:
          <strong>{{ product.type }}</strong> - Product Price:
          <strong>{{ product.price }}</strong> - Product Category:
          <strong>{{ product.category }}</strong> - Product Area:
          <strong>{{ product.area }}</strong>
        </div>
      </li>
    </ul>
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
      region: "",
      // category: "",
      products: [
        {
          region: "Beirut",
          type: "Appartment",
          price: 44,
          category: "Rent",
          area: 253
        },
        {
          region: "Jbeil",
          type: "Room",
          price: 20,
          category: "Buy",
          area: 35
        },
        {
          region: "Jal el dib",
          type: "Chalet",
          price: 399,
          category: "Rent",
          area: 75
        },
        {
          region: "Jbeil",
          type: "Villa",
          price: 599,
          category: "Buy",
          area: 750
        },
        {
          region: "Jounieh",
          type: "Appartment",
          price: 899,
          category: "Buy",
          area: 300
        },
        {
          region: "Beirut",
          type: "House",
          price: 6,
          category: "Rent",
          area: 500
        },
        {
          region: "Tripoli",
          type: "Chalet",
          price: 2,
          category: "Rent",
          area: 300
        },
        {
          region: "Dbayeh",
          type: "Villa",
          price: 7,
          category: "Buy",
          area: 1000
        },
        {
          region: "Rabieh",
          type: "Appartment",
          price: 2,
          category: "Rent",
          area: 150
        },
        {
          region: "Kfardebian",
          type: "Land",
          price: 5000,
          category: "Buy",
          area: 2000
        }
      ]
    };
  },
  computed: {
    filterProducts: function() {
      return this.products.filter(item => {
        return (
          (this.region.length === 0 || item.region.includes(this.region)) &&
          (this.categories.length === 0 ||
            this.categories.includes(item.category)) &&
          (this.types.length === 0 || this.types.includes(item.type))
        );
      });
    }
  }
};
</script>

<style lang="scss" scoped>
#search-box {
  margin-right: auto;
  margin-left: auto;
  justify-content: center;
  display: flex;
}
.is-search-tool {
  margin-right: 5rem;
  margin-left: 5rem;
}
#products-grid {
  display: flex;
  flex-wrap: wrap;
  background-color: antiquewhite;
  margin-top: 3rem;
  padding-top: 1.5rem;
  margin-right: auto;
  margin-left: auto;
  padding-right: 0;
  padding-left: 0;
  width: 100%;
  height: 100%;
  overflow-y: scroll;
}
.hero {
  width: 100%;
  height: 100vh;
  // overflow: hidden;
}
.product-box {
  margin-right: 1rem;
  margin-left: 1rem;
  padding-top: 1rem;
  padding-bottom: 1rem;
  width: 400px;
  height: 400px;
}
.bg-light {
  background-color: aliceblue;
}
.bg-dark {
  background-color: chocolate;
}
</style>

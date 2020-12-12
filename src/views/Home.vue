<template>
  <div class="home">
    <div id="search-box">
      <div class="is-search-tool">
        <h3>Enter Region:</h3>
        <input type="text" v-model="region" placeholder="Region/Location" />
      </div>
      <div class="is-search-tool">
        <h3>Property Type:</h3>
        Villa: <input type="checkbox" value="Villa" v-model="types" /> Room:
        <input type="checkbox" value="Room" v-model="types" /> Appartement:
        <input type="checkbox" value="Appartement" v-model="types" /> Chalet:
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

    <div id="products-grid">
      <ul>
        <li v-for="(product, index) in filterProducts" :key="index">
          Property Region: <strong>{{ product.region }}</strong> - Product Type:
          <strong>{{ product.type }}</strong> - Product Price:
          <strong>{{ product.price }}</strong> - Product Category:
          <strong>{{ product.category }}</strong> - Product Area:
          <strong>{{ product.area }}</strong>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
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
          type: "Appartment",
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
  margin-right: auto;
  margin-left: auto;
  width: 50rem;
}
</style>

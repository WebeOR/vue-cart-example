<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3>Ecosystem</h3>
    <ul>
      <Product-Item
        v-for="product in products"
        :key="product.id"
        :product="product"
        />
    </ul>
  </div>
</template>

<script>

import ProductItem from './ProductItem.vue';

export default {
  name: 'HelloWorld',
  components: {
    ProductItem
  },

  props: {
    'msg': String
  },

  data: () => ({
    products: [
      {
        id: 'vue-router',
        name: 'vue-router',
        link: 'https://router.vuejs.org',
        price: 150,
        quantity: 1,
      },
      {
        id: 'vuex',
        name: 'vuex',
        link: 'https://vuex.vuejs.org',
        price: 200,
        quantity: 1,
      },
      {
        id: 'vue-devtools',
        name: 'vue-devtools',
        link: 'https://github.com/vuejs/vue-devtools#vue-devtools',
        price: 250,
        quantity: 1,
      },
      {
        id: 'vue-loader',
        name: 'vue-loader',
        link: 'https://vue-loader.vuejs.org',
        price: 300,
        quantity: 1,
      },
      {
        id: 'awesome-vue',
        name: 'awesome-vue',
        link: 'https://github.com/vuejs/awesome-vue',
        price: 350,
        quantity: 1,
      },
    ],
  }),

};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

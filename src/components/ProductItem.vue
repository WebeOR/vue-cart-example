<template>
  <li>
    <p>{{ product.name }}</p>
    <a :href="product.link" target="_blank" rel="noopener">{{ product.name }}</a>
    <p>{{ product.price }} руб.</p>
    <button @click="addToCart" type="button">В корзину</button>
  </li>
</template>

<script>

export default {
  name: 'Product-Item',
  props: {
    'product': {
      type: Object,
      required: true,
    }
  },

  methods: {
    addToCart () {
      const { product } = this;
      this.$bus.emit('add-product' , product);
    }
  },
};

</script>

<style lang="scss"></style>
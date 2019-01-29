<template>
  <div class="cart">
    <table>
      <caption>Корзина</caption>
      <thead>
        <tr>
          <th>Наименование</th>
          <th>Кол-во</th>
          <th>Цена</th>
          <th>Сумма</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="product in order"
          :key="product.id">
          <td>{{ product.name }}</td>
          <td>{{ product.quantity }}</td>
          <td>{{ product.price }}</td>
          <td>{{ product.quantity * product.price }}</td>
        </tr>
      </tbody>
    </table>

    <p>Итого: <b>{{ summary }}</b></p>
    <button @click="toCheckOut" :disabled="summary < 1" type="button" >Заказать</button>

    <v-slide :active="showCheckOut">
      <form @submit.prevent="onCheckOut">
        <fieldset>
          <legend>Имя *</legend>
          <input
            id="form_name"
            v-model="form.name"
            name="name"
            type="text"
            placeholder="Имя"
            required
            />
        </fieldset>

        <fieldset>
          <legend>E-mail *</legend>
          <input
            v-model="form.email"
            name="email"
            type="email"
            placeholder="E-mail *"
            required
            />
        </fieldset>

        <fieldset>
          <legend>Телефон *</legend>
          <input
            v-model="form.phone"
            v-mask="'+7 (###) ###-##-##'"
            name="phone"
            type="tel"
            placeholder="Телефон *"
            required
            />
        </fieldset>
        
        <button type="submit">Оставить заявку</button>
      </form>
    </v-slide>
  </div>
</template>

<script>

import { mask } from 'vue-the-mask';

export default {
  name: 'Cart',
  directives: {
    mask
  },

  data: () => ({
    showCheckOut: false,

    order: [],
    form: {
      name: '',
      email: '',
      phone: '',
    }
  }),

  computed: {
    summary () {
      const summs = this.order
        .map( product => product.price * product.quantity )
        .reduce(( accumulator , currentValue ) => (accumulator + currentValue), 0 );
      return summs;
    }
  },

  methods: {
    addProduct (product) {
      const isExist = this.order.find( ord => ord.id === product.id );
      if (isExist) {
        isExist.quantity += 1;
      } else {
        this.order.push(product);
      }
    },

    toCheckOut () {
      console.log('checkOut');
      this.showCheckOut = true;
    },

    onCheckOut () {
      const { form , order } = this;
      console.log('Заказ - ', order );
      console.log('Форма - ', form );
    },

  },

  created () {
    this.$bus.on('add-product' , this.addProduct );
  },

};

</script>

<style lang="scss">

.cart {
  position: fixed;
  top: 0;
  right: 0;
  width: 350px;
  table {
    width: 100%;
  }
  form {
    display: flex;
    flex-direction: column;
  }
}

</style>
<template>
  <section>
    <section class="content">
      <router-link :to="{name: 'Product', params: {id: product.id}}" class="product-link">
        <div>
          <img class="bd-placeholder-img card-img-top" src="https://avatars.mds.yandex.net/get-mpic/4322107/img_id5771335809193590584.jpeg/orig" />
        </div>
        <p>{{ product.name }}</p>
      </router-link>
    </section>
    <section>
      <p class="price">{{ product.price }} ₽</p>
      <div class="btn-group">
        <button @click="addToCart" type="button" class="btn btn-warning btn-cart">В корзину</button>
      </div>
    </section>
  </section>
</template>

<script>
export default {
  name: "product",
  props: ['product'],
  data() {
    return {
      count: 0
    }
  },
  methods: {
    addToCart() {
      const item = {
        id: this.product.id,
        count: 1
      }
      this.$http.post('/cart/add-to-cart', item)
        .then((response) => {
          this.$store.commit("addItem", {id: 10})
        })
    }
  }
}
</script>

<style scoped>

</style>
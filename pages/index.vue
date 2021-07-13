<template>
  <div>
    <Tutorial />

    <div>
      <b-card
        :title="merchant.business_name"
        img-top
        tag="article"
        style="max-width: 20rem;"
        class="mb-2"
      >
        <b-card-text>
          merchant: {{ merchant.business_name }}
          <h3><NuxtLink to="/categories">Categories NuxtLink</NuxtLink></h3>
          <category-list :categories="categories"></category-list>
          <hr />
          <h3><nuxt-link to="/products">Products nuxt-link </nuxt-link></h3>
          <product-list :products="products"></product-list>
        </b-card-text>

        <b-button href="#" variant="primary">Go somewhere</b-button>
      </b-card>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $commerce }) {
    const merchant = await $commerce.merchants.about();
    const { data: categories } = await $commerce.categories.list();
    const { data: products } = await $commerce.products.list();

    return {
      merchant,
      categories,
      products
    };
  }
};
</script>

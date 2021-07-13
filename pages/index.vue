<template>
  <div>
    <Tutorial :products="products" :categories="categories" />
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

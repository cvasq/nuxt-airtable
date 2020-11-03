<template>
  <b-card-group deck>
    <ProductCard
      v-for="product of products"
      :key="product.id"
      :product="product"
    >
    </ProductCard>
  </b-card-group>
</template>

<script>
import ProductCard from '@/components/ProductCard'

export default {
  name: 'ProductCardDeck',
  components: { ProductCard },
  props: ['products'],
}
</script>

<style></style>

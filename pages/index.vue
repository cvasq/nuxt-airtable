<template>
  <div class="container">
    <h1>Nuxt + Aitable</h1>
    <ProductCardDeck :products="products" />
  </div>
</template>

<script>
import ProductCardDeck from '@/components/ProductCardDeck'
import Airtable from 'airtable'

const base = new Airtable({ apiKey: 'AIRBASE_API_KEY' }).base('BASE_API_KEY')
export default {
  components: {
    ProductCardDeck,
  },
  data() {
    return {
      products: [],
    }
  },
  mounted() {
    this.loadData()
  },
  methods: {
    async loadData() {
      this.products = await base('Products')
        .select({ view: 'Grid view' })
        .firstPage()
        .then((response) => {
          const catalog = response.map((item) => item._rawJson)
          return catalog
        })
    },
  },
}
</script>

<style></style>

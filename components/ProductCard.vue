<template>
  <b-card :title="product.fields.Name">
    <b-card-img
      :scr="product.fields.Attachments[0].url"
      :alt="product.fields.Name"
      top
    ></b-card-img>
    <b-card-img :scr="product.fields.Attachments[0].url"></b-card-img>
    <b-card-text>
      {{ product.fields.Notes }}
    </b-card-text>
    <b-button href="#" variant="white" disabled>{{ formattedPrice }}</b-button>
    <template #footer>
      <small class="text-muted">{{ quantityConditional }}</small>
    </template>
  </b-card>
</template>

<script>
export default {
  name: 'ProductCard',
  props: ['product'],
  computed: {
    cardImage() {
      return this.product.fields.Attachments[0].url
    },
    formattedPrice() {
      return 'R$' + this.product.fields.price.toFixed(2).replace('.', ',')
    },
    quantityConditional() {
      return this.product.fields.qtde === 0
        ? 'ESGOTADO'
        : this.product.fields.qtde + ' em estoque'
    },
  },
}
</script>

<style>
img[class^='card-img'] {
  object-fit: contain;
}
</style>

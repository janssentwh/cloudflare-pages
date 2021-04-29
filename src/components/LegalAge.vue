<template>
  <div class="legal-age modal">
    Are you over 18 years and allowed to drink?
    <button>Yes</button>
    <button>No</button>
  </div>
</template>

<script>
export default {
  metaInfo () {
    return {
      title: this.$page.shopifyProduct.title
    }
  },
  data: () => ({
    quantity: 1
  }),
  computed: {
    product () { return this.$page.shopifyProduct },
    productOptions () { return this.product.options.filter(({ name }) => name !== 'Title') },
    currentVariant () {
      const matchedVariant = this.product.variants.find(variant =>
        variant.selectedOptions.every(({ name, value }) => value === this.selectedOptions[ name ])
      )
      return matchedVariant
    }
  },
  watch: {
    $route (to, from) {
      const [firstVariant] = this.product.variants
      this.selectedOptions = firstVariant.selectedOptions.reduce((options, { name, value }) => ({ [ name ]: value, ...options }), {})
    }
  },
  mounted () {
    const [firstVariant] = this.product.variants
    this.selectedOptions = firstVariant.selectedOptions.reduce((options, { name, value }) => ({ [ name ]: value, ...options }), {})
  },
  methods: {
    async addToCart () {

    }
  }
}
</script>
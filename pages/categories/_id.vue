<template>
  <div>
    <nuxt-child :category="category" />
  </div>
</template>

<script>
import categories from '@/data/categories'
export default {
  asyncData({ params }) {
    return {
      category: categories.find((c) => c.id === parseInt(params.id)),
    }
  },
}
</script>

<style></style>

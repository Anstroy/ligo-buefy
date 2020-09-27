<template>
  <div>
    <RetosView :retos="retos" />
  </div>
</template>

<script>
import RetosView from '@/components/Retos'
const retos = require('~/data/retos')
const categories = require('~/data/categories')
const profiles = require('~/data/profiles')

export default {
  components: {
    RetosView,
  },
  data: () => ({
    data: [
      'Angular',
      'Angular 2',
      'Aurelia',
      'Backbone',
      'Ember',
      'jQuery',
      'Meteor',
      'Node.js',
      'Polymer',
      'React',
      'RxJS',
      'Vue.js',
    ],
    name: '',
    selected: null,
    retos,
    reto: null,
  }),

  methods: {
    retoClick(e) {
      this.reto = e
    },
  },

  computed: {
    findPublisher() {
      return profiles.find((x) => x.id === this.reto.publisher)
    },

    filterCategories() {
      return this.reto.categories.map((c) => categories.find((x) => x.id === c))
    },

    filteredDataArray() {
      return this.data.filter((option) => {
        return (
          option.toString().toLowerCase().indexOf(this.name.toLowerCase()) >= 0
        )
      })
    },
  },
}
</script>

<style></style>

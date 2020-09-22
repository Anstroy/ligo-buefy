<template>
  <div>
    <section>
      <p class="content"><b>Selected:</b> {{ selected }}</p>
      <b-field label="Find a JS framework">
        <b-autocomplete
          rounded
          v-model="name"
          :data="filteredDataArray"
          placeholder="e.g. jQuery"
          icon="magnify"
          clearable
          @select="(option) => (selected = option)"
        >
          <template slot="empty">No results found</template>
        </b-autocomplete>
      </b-field>
    </section>
    <div class="columns">
      <!-- LEFT -->
      <div class="column">
        <div
          @click="retoClick(reto)"
          v-for="reto in retos"
          :key="reto.id"
          class="card mb-3 cursor-pointer"
        >
          <div class="card-content">
            <h3 class="title is-4">{{ reto.title }}</h3>
          </div>
        </div>
      </div>

      <!-- RIGHT -->
      <div class="column is-relative">
        <div class="is-sticky" style="top: 0">
          <div class="card mt-6" v-if="reto">
            <div class="card-content">
              <h3 class="title is-4">{{ reto.title }}</h3>
              <p>{{ reto.description }}</p>
              <br />
              <b-taglist attached>
                <b-tag type="is-dark"><i class="bx bx-user"></i></b-tag>
                <b-tag type="is-info">{{ findPublisher.name }}</b-tag>
              </b-taglist>
              <br />
              <b-taglist>
                <b-tag
                  type="is-info"
                  v-for="(cat, i) in filterCategories"
                  :key="i"
                  >{{ cat.title }}</b-tag
                >
              </b-taglist>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const retos = require('~/data/retos')
const categories = require('~/data/categories')
const profiles = require('~/data/profiles')

export default {
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

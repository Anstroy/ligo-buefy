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
          class="card mb-3"
        >
          <div class="card-content">
            <h3 class="title is-4">{{ reto.title }}</h3>
          </div>
        </div>
      </div>

      <!-- RIGHT -->
      <div class="column is-relative">
        <div style="position: sticky; top: 0">
          <div class="card mt-6">
            <div class="card-content">
              <h3 class="title is-4">{{ reto.title }}</h3>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const retos = require('~/data/retos')

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
    reto: Object,
  }),

  methods: {
    retoClick(e) {
      this.reto = e
    },
  },

  computed: {
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

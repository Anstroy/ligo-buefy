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
        <div class="card card-content">
          <h3 class="title is-4">Reto 1</h3>
        </div>
      </div>

      <!-- RIGHT -->
      <div class="column"></div>
    </div>
  </div>
</template>

<script>
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
  }),

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

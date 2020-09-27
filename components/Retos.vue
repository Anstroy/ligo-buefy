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
    <br />
    <div class="columns">
      <!-- LEFT -->
      <div class="column">
        <div
          v-for="r in retos"
          :key="r.id"
          @click="retoClick(r)"
          class="mb-3 cursor-pointer"
        >
          <div class="box">
            <article class="media">
              <div class="media-left">
                <figure class="image is-64x64">
                  <img
                    src="https://bulma.io/images/placeholders/128x128.png"
                    alt="Image"
                  />
                </figure>
              </div>
              <div class="media-content">
                <div class="content">
                  <p>
                    <strong>{{ r.title }}</strong>
                    <small>31m</small>
                    <br />
                    {{ r.description }}
                  </p>
                </div>
                <nav class="level is-mobile">
                  <div class="level-left">
                    <a class="level-item" aria-label="reply">
                      <span class="icon is-small">
                        <i class="fas fa-reply" aria-hidden="true"></i>
                      </span>
                    </a>
                    <a class="level-item" aria-label="retweet">
                      <span class="icon is-small">
                        <i class="fas fa-retweet" aria-hidden="true"></i>
                      </span>
                    </a>
                    <a class="level-item" aria-label="like">
                      <span class="icon is-small">
                        <i class="fas fa-heart" aria-hidden="true"></i>
                      </span>
                    </a>
                  </div>
                </nav>
              </div>
            </article>
          </div>
        </div>
      </div>

      <!-- RIGHT -->
      <div class="column is-relative">
        <div class="is-sticky" style="top: 0">
          <div class="card mt-6" v-if="reto !== null">
            <div class="card-content">
              <h3 class="title is-4">{{ reto.title }}</h3>
              <p>{{ reto.description }}</p>
              <br />
              <b-navbar-item
                tag="router-link"
                :to="{ path: '/profiles/' + findPublisher.slug }"
              >
                <b-taglist attached>
                  <b-tag type="is-dark"><i class="bx bx-user"></i></b-tag>
                  <b-tag type="is-info">{{ findPublisher.name }}</b-tag>
                </b-taglist>
              </b-navbar-item>
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
const categories = require('~/data/categories')
const profiles = require('~/data/profiles')

export default {
  props: ['retos'],
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
      //   return profiles.find((x) => x.id === 1)
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

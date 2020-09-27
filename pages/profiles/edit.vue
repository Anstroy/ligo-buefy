<template>
  <b-tabs v-model="activeTab" position="is-centered">
    <template v-for="tab in tabs">
      <b-tab-item
        @click="propertyClick(property)"
        v-if="tab.displayed"
        :key="tab.id"
        :value="tab.id"
        :label="tab.label"
      >
        <div class="columns">
          <div class="column">
            <div class="box">
              {{ tab.content }}
            </div>
          </div>
        </div>
      </b-tab-item>
    </template>
  </b-tabs>
</template>

<script>
const estudios = require('~/data/estudios')
const certificaciones = require('~/data/certificaciones')
const profiles = require('~/data/profiles')
const categories = require('~/data/categories')
const especializaciones = require('~/data/especializaciones')

export default {
  data: () => ({
    property: 0,
  }),

  methods: {
    propertyClick(e) {
      console.log(e)
      this.property = e
    },
  },

  computed: {
    baseTabs() {
      return [
        {
          id: 'areas',
          label: 'Áreas de especializacion',
          content: 'this.findPublisher.name',
          displayed: true,
        },
        {
          id: 'estudios',
          label: 'Estudios',
          content: 'Music: Lorem ipsum dolor sit amet.',
          displayed: true,
        },
        {
          id: 'certs',
          label: 'Certificaciones',
          content: 'Videos: Lorem ipsum dolor sit amet.',
          displayed: true,
        },
        {
          id: 'general',
          label: 'Informacion general y de contacto',
          content: 'Games: Lorem ipsum dolor sit amet.',
          displayed: true,
        },
        {
          id: 'reconocimientos',
          label: 'Reconocimientos',
          content: 'Comics: Lorem ipsum dolor sit amet.',
          displayed: true,
        },
        {
          id: 'aliados',
          label: 'Red de aliados',
          content: 'Movies: Lorem ipsum dolor sit amet.',
          displayed: true,
        },
      ]
    },
    tabs() {
      return [...this.baseTabs]
    },

    findPublisher() {
      return profiles.find((x) => x.id === this.property.publisher)
    },

    filterCategories() {
      return this.reto.categories.map((c) => categories.find((x) => x.id === c))
    },

    findStudies() {
      return estudios.find((x) => x.id === this.property.estudios)
    },

    findCertificaciones() {
      return certificaciones.find((x) => x.id === this.property.certificaciones)
    },

    findEspecializaciones() {
      return especializaciones.find(
        (x) => x.id === this.property.especializaciones
      )
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

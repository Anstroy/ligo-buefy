<template>
  <b-navbar>
    <template slot="brand">
      <b-navbar-item tag="router-link" :to="{ path: '/' }">
        <img
          src="/images/ligo.png"
          alt="Lightweight UI components for Vue.js based on Bulma"
        />
      </b-navbar-item>
    </template>
    <template slot="start">
      <b-navbar-item href="#"> Home </b-navbar-item>
      <b-navbar-item active="true" tag="router-link" :to="{ path: '/retos' }">
        Retos
      </b-navbar-item>
      <b-navbar-dropdown label="Info">
        <b-navbar-item href="#"> About </b-navbar-item>
        <b-navbar-item href="#"> Contact </b-navbar-item>
      </b-navbar-dropdown>
    </template>

    <template slot="end">
      <b-navbar-item tag="div">
        <div class="buttons">
          <b-button
            tag="router-link"
            :to="{ path: '/auth/register' }"
            type="is-primary"
          >
            <strong>Sign up</strong>
          </b-button>
          <b-button
            tag="router-link"
            :to="{ path: '/auth/login' }"
            type="is-light"
          >
            Log in
          </b-button>
        </div>
      </b-navbar-item>
    </template>
  </b-navbar>
</template>
<script>
export default {}
</script>

<style></style>

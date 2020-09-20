<template>
  <client-only>
    <div class="card">
      <div class="card-content">
        <h1 class="title">{{ title }}</h1>
        <section>
          <b-field label="Username" message="This username is available">
            <b-input value="johnsilver" maxlength="30"></b-input>
          </b-field>

          <b-field label="Password">
            <b-input type="password" value="iwantmytreasure" password-reveal>
            </b-input>
          </b-field>

          <b-field>
            <b-checkbox>Basic</b-checkbox>
          </b-field>

          <b-field>
            <b-button type="is-primary">{{ title }}</b-button>
          </b-field>
        </section>
      </div>
    </div>
  </client-only>
</template>

<script>
export default {
  name: 'AuthForm',
  props: ['title'],
  data() {
    return {}
  },
}
</script>

<style></style>

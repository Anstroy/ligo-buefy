<template>
  <AuthForm :title="title" />
</template>

<script>
import AuthForm from '~/components/Forms/Auth'
export default {
  components: {
    AuthForm,
  },
  data() {
    return {
      title: 'Register',
    }
  },
}
</script>

<style></style>

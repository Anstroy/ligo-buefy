<template>
  <div>
    <nuxt-child :profile="profile" />
  </div>
</template>

<script>
import profiles from '@/data/profiles'
export default {
  asyncData({ params }) {
    return {
      profile: profiles.find((p) => p.slug == params.slug),
    }
  },
}
</script>

<style></style>

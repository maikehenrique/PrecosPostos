<template>
  <div>
    <client-only>
      <Toast />
    </client-only>
    <Nuxt />
  </div>
</template>
<script>
export default {
  name: 'LayoutDefault',
  watch: {
    $route() {
      this.$toast.removeAllGroups()
    },
  },
}
</script>

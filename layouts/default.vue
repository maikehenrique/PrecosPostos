<template>
  <div>
    <client-only>
      <Toast />
    </client-only>
    <Menubar :model="items">
      <template #start>
        <div class="menu-title-logo">
          <div>
            <img
              alt="logo"
              src="../static/logo4.png"
              height="50"
              class="mr-2 mt-1"
            />
          </div>
          <div>
            <h3>Preço Fácil</h3>
          </div>
        </div>
      </template>
      <template #end> </template>
    </Menubar>
    <Nuxt />
  </div>
</template>
<script>
export default {
  name: 'LayoutDefault',
  data() {
    return {
      items: [
        {
          label: 'Home',
          icon: 'pi pi-fw pi-home',
        },
        {
          label: 'Fale Conosco',
          icon: 'pi pi-fw pi-comments',
        },
        {
          label: 'Sobre',
          icon: 'pi pi-fw pi-book',
        },
      ],
    }
  },
  watch: {
    $route() {
      this.$toast.removeAllGroups()
    },
  },
}
</script>
<style scoped>
.menu-title-logo {
  display: flex;
}
</style>

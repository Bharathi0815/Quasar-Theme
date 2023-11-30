<template>
  <q-layout view=" hHh lpr fFf">
    hHh lpr fFf
    <q-header flat>
      <q-toolbar>
        <q-icon name="store" size="lg"></q-icon>

        <q-toolbar-title> Shopify </q-toolbar-title>
        <q-input
          class="search-input"
          outlined
          dense
          v-model="searchInput"
          placeholder="Search..."
        />
        <q-icon name="search-icon"></q-icon>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      :width="250"
      show-if-above
      bordered
      class="drawer-background"
    >
      <q-list>
        <!-- Navigation item1-->
        <q-item
          v-for="nav in navs"
          :key="nav.label"
          :to="nav.to"
          exact
          clickable
        >
          <q-item-section avatar>
            <q-icon :name="nav.icon" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ nav.label }}</q-item-label>
          </q-item-section>
        </q-item>

        <!-- Navigation item2-->
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "MainLayout",

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
      // Array for Navigation links to dynamically pass the values
      navs: [
        {
          label: "Home",
          icon: "home",
          to: "/",
        },
        {
          label: "Orders",
          icon: "shopping_cart",
          to: "/orders",
        },
      ],
    };
  },
});
</script>
<style lang="scss">
.search-input {
  border: 1px solid #ccc;

  border-radius: 4px;
  border-color: white;
  width: 300px;
}

.drawer-background {
  background-color: $cyan-1;
}
</style>

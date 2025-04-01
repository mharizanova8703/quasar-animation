<template>
  <q-layout>
    <!-- Navbar -->
    <q-header elevated class="bg-dark-green">
      <q-toolbar>
        <!-- Logo -->
     
        <q-img src="/camping-logo.png" class="logo q-mr-sm" />

        <q-toolbar-title >Camping Guide <img class="favicon-w" src="favicon.png"></q-toolbar-title>

        <!-- Desktop Navigation -->
        <q-space />
     
      </q-toolbar>
    </q-header>

    <!-- Mobile Drawer Navigation -->
    <q-drawer
      v-model="drawer"
      side="left"
      overlay
      class="bg-dark-green text-white"
    >
    </q-drawer>
  </q-layout>
</template>

<script setup>
import { ref } from "vue";

const drawer = ref(false);
const toggleDrawer = () => {
  drawer.value = !drawer.value;
};
</script>

<style  scoped lang="scss">
.bg-dark-green {
  color: $primary-yellow;
  background-color: $dark-green;
}
.favicon-w{
  width:30px;
  margin: 0 10px;
}
.q-layout {
    color: #d9c251;
  height: auto !important;
  min-height: unset !important;
}
.q-toolbar-title{
  display: flex;
  align-items: center;
  margin: 0 10px;
  color: $primary-yellow;
}
.logo {
  width: 40px;
  height: 40px;
  border-radius: 50%;
}
.ellipsis {
display: flex;
}
</style>

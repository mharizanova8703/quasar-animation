<template>
  <q-layout>
    <!-- Navbar -->
    <q-header elevated class="bg-dark-green text-white">
      <q-toolbar>
        <!-- Logo -->
        <q-btn
          flat
          dense
          round
          icon="menu"
          @click="toggleDrawer"
          class="q-mr-md q-md-hide"
        />
        <q-img src="/camping-logo.png" class="logo q-mr-sm" />

        <q-toolbar-title class="text-bold">Camping Guide</q-toolbar-title>

        <!-- Desktop Navigation -->
        <q-space />
        <q-tabs class="q-md-flex q-none">
          <q-route-tab to="/" label="Home" />
          <q-route-tab to="/menu" label="Menu" />
          <q-route-tab to="/plan" label="Plan" />
          <q-route-tab to="/snacks" label="Snacks" />
          <q-route-tab to="/gear" label="Gear & Shoes" />
          <q-route-tab to="/fire" label="Fire & Safety" />
          <q-route-tab to="/wildlife" label="Wildlife" />
        </q-tabs>
      </q-toolbar>
    </q-header>

    <!-- Mobile Drawer Navigation -->
    <q-drawer
      v-model="drawer"
      side="left"
      overlay
      class="bg-dark-green text-white"
    >
      <q-list>
        <q-item-label header>Camping Guide</q-item-label>
        <q-item clickable v-ripple to="/" @click="toggleDrawer">
          <q-item-section>Home</q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/menu" @click="toggleDrawer">
          <q-item-section>Menu</q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/plan" @click="toggleDrawer">
          <q-item-section>Plan</q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/snacks" @click="toggleDrawer">
          <q-item-section>Snacks</q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/gear" @click="toggleDrawer">
          <q-item-section>Gear & Shoes</q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/fire" @click="toggleDrawer">
          <q-item-section>Fire & Safety</q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/wildlife" @click="toggleDrawer">
          <q-item-section>Wildlife</q-item-section>
        </q-item>
      </q-list>
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

<style scoped>
.bg-dark-green {
  background-color: #1c3b24; /* Deep Army Green */
}
.q-layout {
  height: auto !important;
  min-height: unset !important;
}
.logo {
  width: 40px;
  height: 40px;
  border-radius: 50%;
}
</style>

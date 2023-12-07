<script setup>
import { ref } from 'vue';

const leftDrawerOpen = ref(false);

const toggleLeftDrawer = () => (leftDrawerOpen.value = !leftDrawerOpen.value);
</script>

<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="text-white" height-hint="98" style="background-color: #4169e1">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" class="lt-md" />
        <q-toolbar-title class="row">
          <q-avatar size="60px">
            <img src="/chillspotz_logo.svg" />
          </q-avatar>
          <span class="header q-pt-md">Chillspotz</span>
        </q-toolbar-title>
      </q-toolbar>

      <q-tabs align="left" class="gt-sm">
        <q-route-tab to="/" label="Home" />
        <q-route-tab to="/impressum" label="Impressum" />
      </q-tabs>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" side="left" bordered>
      <q-tabs vertical>
        <q-route-tab to="/" label="Home" icon="fa-solid fa-home" />
        <q-route-tab to="/impressum" label="Impressum" icon="fa-solid fa-info" />
      </q-tabs>
    </q-drawer>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<style>
body {
  background-color: #00bd25;
}

* {
  font-family: 'Montserrat';
}

.header {
  font-family: 'Forte';
  src: url('/fonts/Forte.tff') format('truetype');
  color: black;
}
</style>

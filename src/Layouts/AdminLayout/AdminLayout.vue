<template>
    <div class="app">
      <SideBarAdmin />
      <div class="d-block w-100" style="padding-left: 230px;">
        <AppHeaderAdmin />
        <router-view />
      </div>
    </div>
  </template>
  <script setup>
  import SideBarAdmin from "../../components/SideBarAdmin/SideBarAdmin.vue";
  import AppHeaderAdmin from "../../components/AppHeaderAdmin/AppHeaderAdmin.vue";
  </script>
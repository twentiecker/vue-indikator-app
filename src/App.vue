<script setup>
import { RouterView } from "vue-router";
</script>

<template>
  <router-view v-slot="{ Component }">
    <!-- Use any custom transition and  to `fade` -->
    <transition name="fade" mode="out-in">
      <component :is="Component" :key="$route.path" />
    </transition>
  </router-view>
</template>

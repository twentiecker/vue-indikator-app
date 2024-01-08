<script setup>
import Graph from './components/Graph.vue';
import { ref } from 'vue';

const isDark = ref(false);
const bodyClass = ref('body');
const modeTitle = ref('Dark Mode');
const switchMode = () => {
  isDark.value = !isDark.value;
  if (isDark.value) {
    bodyClass.value = 'body dark';
    modeTitle.value = 'Light Mode';
  } else {
    bodyClass.value = 'body';
    modeTitle.value = 'Dark Mode';
  }
};
const isClose = ref(false);
const sidebarClass = ref('sidebar');
const toggleSidebar = () => {
  isClose.value = !isClose.value;
  if (isClose.value) {
    sidebarClass.value = 'sidebar close';
  } else {
    sidebarClass.value = 'sidebar';
  }
};
const openSidebar = () => {
  isClose.value = false;
  sidebarClass.value = 'sidebar';
};
</script>

<template>
  <div :class="bodyClass">
    <nav :class="sidebarClass">
      <header>
        <div class="image-text">
          <span class="image">
            <img src="./assets/bps.png" alt="bps" />
          </span>
          <div class="text header-text">
            <span class="line1">Neraca</span>
            <span class="line2">Pengeluaran</span>
          </div>
        </div>
        <i @click="toggleSidebar" class="bx bx-chevron-right toggle"></i>
      </header>
      <div class="menu-bar">
        <div class="menu">
          <li @click="openSidebar" class="search-box">
            <i class="bx bx-search icon"></i>
            <input type="text" placeholder="Search..." />
          </li>
          <ul class="menu-links">
            <li class="nav-link">
              <a href="">
                <i class="bx bx-home-alt icon"></i>
                <span class="text nav-text">Dashboard</span>
              </a>
            </li>
            <li class="nav-link">
              <a href="">
                <i class="bx bx-edit-alt icon"></i>
                <span class="text nav-text">Input</span>
              </a>
            </li>
          </ul>
        </div>
        <div class="bottom-content">
          <li class="nav-link">
            <a href="">
              <i class="bx bx-log-out icon"></i>
              <span class="text nav-text">Logout</span>
            </a>
          </li>
          <li class="mode">
            <div class="moon-sun">
              <i class="bx bx-moon icon moon"></i>
              <i class="bx bx-sun icon sun"></i>
            </div>
            <span class="mode-text text">{{ modeTitle }}</span>
            <div class="toggle-switch">
              <span @click="switchMode" class="switch"></span>
            </div>
          </li>
        </div>
      </div>
    </nav>

    <section class="home">
      <div class="text">Dashboard</div>
      <Graph />
    </section>
  </div>
</template>

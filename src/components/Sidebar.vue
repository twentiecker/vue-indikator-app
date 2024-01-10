<script setup>
import { RouterLink, RouterView, useRouter, useRoute } from "vue-router";
import { store } from "../store";
import { ref } from "vue";

const router = useRouter();
const route = useRoute();
const logout = async () => {
  localStorage.clear();
  store.updateHasLogin(false);
  store.updateName(null);
  router.push("/login");
};

const isDark = ref(false);
const bodyClass = ref("body");
const modeTitle = ref("Dark Mode");
const switchMode = () => {
  isDark.value = !isDark.value;
  if (isDark.value) {
    bodyClass.value = "body dark";
    modeTitle.value = "Light Mode";
  } else {
    bodyClass.value = "body";
    modeTitle.value = "Dark Mode";
  }
};

const isClose = ref(false);
const sidebarClass = ref("sidebar");
const toggleSidebar = () => {
  isClose.value = !isClose.value;
  if (isClose.value) {
    sidebarClass.value = "sidebar close";
  } else {
    sidebarClass.value = "sidebar";
  }
};
const openSidebar = () => {
  isClose.value = false;
  sidebarClass.value = "sidebar";
};
</script>

<template>
  <div :class="bodyClass">
    <nav :class="sidebarClass">
      <header>
        <div class="image-text">
          <span class="image">
            <img src="../assets/bps.png" alt="bps" />
          </span>
          <div class="text header-text">
            <span class="line1">Indikator Neraca</span>
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
              <a href="#">
                <i class="bx bx-home-alt icon"></i>
                <span class="text nav-text">Domestik</span>
              </a>
            </li>
          </ul>
        </div>
        <div class="bottom-content">
          <li class="nav-link">
            <a @click="logout" href="#">
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
      <!-- <div class="text">Mobilitas dan Pariwisata</div> -->
      <slot></slot>
    </section>
  </div>
</template>

<style scoped>
.body {
  height: 100vh;
  background: var(--body-color);
  transition: var(--tran-05);
}

.body.dark {
  /* Colors */
  --body-color: #18191a;
  --sidebar-color: #242526;
  --primary-color: #3a3b3c;
  --primary-color-light: #3a3b3c;
  --toggle-color: #fff;
  --text-color: #ccc;
}

.sidebar {
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  width: 250px;
  padding: 10px 14px;
  background-color: var(--sidebar-color);
  transition: var(--tran-05);
  z-index: 100;
}

.sidebar.close {
  width: 88px;
}

.sidebar .text {
  font-size: 16px;
  font-weight: 500;
  color: var(--text-color);
  transition: var(--tran-03);
  white-space: nowrap;
  opacity: 1;
}

.sidebar.close .text {
  opacity: 0;
}

.sidebar .image {
  min-width: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.sidebar li {
  height: 50px;
  margin-top: 10px;
  list-style: none;
  display: flex;
  align-items: center;
}

.sidebar li .icon {
  display: flex;
  align-items: center;
  justify-content: center;
  min-width: 60px;
  font-size: 20px;
}

.sidebar li .icon,
.sidebar li .text {
  color: var(--text-color);
  transition: var(--tran-02);
}

.sidebar header {
  position: relative;
}

.sidebar .image-text img {
  width: 40px;
  border-radius: 6px;
}

.sidebar header .image-text {
  display: flex;
  align-items: center;
}

header .image-text .header-text {
  display: flex;
  flex-direction: column;
}

.header-text .line1 {
  font-weight: 600;
}

.header-text .line2 {
  font-weight: 600;
  margin-top: -2px;
}

.sidebar header .toggle {
  position: absolute;
  top: 50%;
  right: -25px;
  transform: translateY(-50%) rotate(180deg);
  height: 25px;
  width: 25px;
  background: var(--primary-color);
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  color: var(--sidebar-color);
  font-size: 22px;
  transition: var(--tran-03);
  cursor: pointer;
}

.sidebar.close header .toggle {
  transform: translateY(-50%);
}

.body.dark .sidebar header .toggle {
  color: var(--text-color);
}

.sidebar .menu {
  margin-top: 35px;
}

.sidebar .search-box {
  background: var(--primary-color-light);
  border-radius: 6px;
  transition: var(--tran-05);
}

.search-box input {
  height: 100%;
  width: 100%;
  outline: none;
  border: none;
  border-radius: 6px;
  font-size: 16px;
  font-weight: 500;
  background: var(--primary-color-light);
  transition: var(--tran-05);
  color: var(--text-color);
}

.sidebar li a {
  height: 100%;
  width: 100%;
  display: flex;
  align-items: center;
  text-decoration: none;
  border-radius: 6px;
  transition: var(--tran-04);
}

.sidebar li a:hover {
  background: var(--primary-color);
}

.sidebar li a:hover .icon,
.sidebar li a:hover .text {
  color: var(--sidebar-color);
}

.body.dark .sidebar li a:hover .icon,
.body.dark .sidebar li a:hover .text {
  color: var(--text-color);
}

.sidebar .menu-bar {
  height: calc(100% - 50px);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.menu-bar .mode {
  position: relative;
  border-radius: 6px;
  background: var(--primary-color-light);
  transition: var(--tran-05);
}

.menu-bar .mode .moon-sun {
  height: 50px;
  width: 60px;
  display: flex;
  align-items: center;
}

.menu-bar .mode i {
  position: absolute;
}

.menu-bar .mode i.sun {
  opacity: 0;
}

.body.dark .menu-bar .mode i.sun {
  opacity: 1;
}

.body.dark .menu-bar .mode i.moon {
  opacity: 0;
}

.menu-bar .mode .toggle-switch {
  position: absolute;
  right: 0px;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  min-width: 60px;
  cursor: pointer;
  border-radius: 6px;
  background: var(--primary-color-light);
  transition: var(--tran-05);
}

.toggle-switch .switch {
  position: relative;
  height: 22px;
  width: 44px;
  border-radius: 25px;
  background: var(--toggle-color);
  transition: var(--tran-05);
}

.switch::before {
  content: "";
  position: absolute;
  height: 15px;
  width: 15px;
  border-radius: 50%;
  top: 50%;
  left: 5px;
  transform: translateY(-50%);
  background: var(--sidebar-color);
  transition: var(--tran-03);
}

.body.dark .switch::before {
  left: 25px;
}

/* Section */
.home {
  position: relative;
  height: 100%;
  left: 250px;
  width: calc(100% - 250px);
  background: var(--body-color);
  transition: var(--tran-05);
}

/* .home .text {
  font-size: 30px;
  font-weight: 500;
  color: var(--text-color);
  padding: 8px 40px;
} */

.sidebar.close ~ .home {
  left: 88px;
  width: calc(100% - 88px);
}
</style>

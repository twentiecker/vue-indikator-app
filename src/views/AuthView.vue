<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
import {
  useFetch,
  hasErrorOccured,
  errorMessage,
  usernameError,
  emailError,
  passwordError,
  turnOffError,
  passwordErrorMessge,
} from "../fetch";
import { store } from "../store";

const user = ref({
  username: null,
  email: null,
  password: null,
});

const router = useRouter();

const hideAllErrors = () => {
  turnOffError();
};

const handleAuthLogin = async () => {
  try {
    await useFetch(`auth/login/`, user.value);
    if (store.hasLogin) router.push("/");
  } catch (err) {
    console.log(err);
  }
};

const handleAuthRegister = async () => {
  try {
    await useFetch(`auth/register/`, user.value);
    if (store.hasLogin) router.push("/");
  } catch (err) {
    console.log(err);
  }
};

const isActive = ref(false);
const containerClass = ref("container");
const toggleContainer = () => {
  isActive.value = !isActive.value;
  if (isActive.value) {
    containerClass.value = "container active";
  } else {
    containerClass.value = "container";
  }
};
</script>

<template>
  <div class="body">
    <div :class="containerClass" id="container">
      <div class="form-container sign-up">
        <form @submit.prevent="handleAuthRegister" @click="hideAllErrors">
          <h1>Create Account</h1>
          <div class="social-icons">
            <a href="#" class="icon">
              <i class="bx bxl-google-plus"></i>
            </a>
            <a href="#" class="icon">
              <i class="bx bxl-facebook"></i>
            </a>
            <a href="#" class="icon">
              <i class="bx bxl-github"></i>
            </a>
            <a href="#" class="icon">
              <i class="bx bxl-linkedin"></i>
            </a>
          </div>
          <span>or use your email for registration</span>
          <input v-model="user.username" type="text" placeholder="Name" />
          <input v-model="user.email" type="email" placeholder="Email" />
          <input
            v-model="user.password"
            type="password"
            placeholder="Password"
          />
          <button type="submit">Sign Up</button>
        </form>
      </div>
      <div class="form-container sign-in">
        <form @submit.prevent="handleAuthLogin" @click="hideAllErrors">
          <h1>Sign In</h1>
          <div class="social-icons">
            <a href="#" class="icon">
              <i class="bx bxl-google-plus"></i>
            </a>
            <a href="#" class="icon">
              <i class="bx bxl-facebook"></i>
            </a>
            <a href="#" class="icon">
              <i class="bx bxl-github"></i>
            </a>
            <a href="#" class="icon">
              <i class="bx bxl-linkedin"></i>
            </a>
          </div>
          <span>or use your email password</span>
          <input v-model="user.email" type="email" placeholder="Email" />
          <input
            v-model="user.password"
            type="password"
            placeholder="Password"
          />
          <a href="#">Forget Your Password?</a>
          <button type="submit">Sign In</button>
        </form>
      </div>
      <div class="toggle-container">
        <div class="toggle">
          <div class="toggle-panel toggle-left">
            <h1>Welcome Back!</h1>
            <p>Enter your personal details to use all of site features</p>
            <button @click="toggleContainer" class="hidden" id="login">
              Sign In
            </button>
          </div>
          <div class="toggle-panel toggle-right">
            <h1>Hello, Friend!</h1>
            <p>
              Register with your personal details to use all of site features
            </p>
            <button @click="toggleContainer" class="hidden" id="register">
              Sign Up
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.body {
  background-color: #c9d6ff;
  background: linear-gradient(to right, #e2e2e2, #c9d6ff);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  height: 100vh;
}

.container {
  background-color: #fff;
  border-radius: 30px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.35);
  position: relative;
  overflow: hidden;
  width: 768px;
  max-width: 100%;
  min-height: 480px;
}

.container p {
  font-size: 14px;
  line-height: 20px;
  letter-spacing: 0.3px;
  margin: 20px 0;
}

.container span {
  font-size: 12px;
}

.container a {
  color: #333;
  font-size: 13px;
  text-decoration: none;
  margin: 15px 0 10px;
}

.container button {
  background-color: #512da8;
  color: #fff;
  font-size: 12px;
  padding: 10px 45px;
  border: 1px solid transparent;
  border-radius: 8px;
  font-weight: 600;
  letter-spacing: 0.5px;
  text-transform: uppercase;
  margin-top: 10px;
  cursor: pointer;
}

.container button.hidden {
  background-color: transparent;
  border-color: #fff;
}

.container form {
  background-color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  padding: 0 40px;
  height: 100%;
}

.container input {
  background-color: #eee;
  border: none;
  margin: 8px 0;
  padding: 10px 15px;
  font-size: 13px;
  border-radius: 8px;
  width: 100%;
  outline: none;
}

.form-container {
  position: absolute;
  top: 0;
  height: 100%;
  transition: all 0.6s ease-in-out;
}

.sign-in {
  left: 0;
  width: 50%;
  z-index: 2;
}

.container.active .sign-in {
  transform: translateX(100%);
}

.sign-up {
  left: 0;
  width: 50%;
  opacity: 0;
  z-index: 1;
}

.container.active .sign-up {
  transform: translateX(100%);
  opacity: 1;
  z-index: 5;
  animation: move 0.6s;
}

@keyframes move {
  0%,
  49.99% {
    opacity: 0;
    z-index: 1;
  }
  50%,
  100% {
    opacity: 1;
    z-index: 5;
  }
}

.social-icons {
  margin: 20px 0;
}

.social-icons a {
  border: 1px solid #ccc;
  border-radius: 20%;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  margin: 0 3px;
  width: 40px;
  height: 40px;
}

.toggle-container {
  position: absolute;
  top: 0;
  left: 50%;
  width: 50%;
  height: 100%;
  overflow: hidden;
  transition: all 0.6s ease-in-out;
  border-radius: 150px 0 0 100px;
  z-index: 1000;
}

.container.active .toggle-container {
  transform: translateX(-100%);
  border-radius: 0 150px 100px 0;
}

.toggle {
  background-color: #512da8;
  height: 100%;
  background: linear-gradient(to right, #5c6bc0, #512da8);
  color: #fff;
  position: relative;
  left: -100%;
  height: 100%;
  width: 200%;
  transform: translateX(0);
  transition: all 0.6s ease-in-out;
}

.container.active .toggle {
  transform: translateX(50%);
}

.toggle-panel {
  position: absolute;
  width: 50%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  padding: 0 30px;
  text-align: center;
  top: 0;
  transform: translateX(0);
  transition: all 0.6s ease-in-out;
}

.toggle-left {
  transform: translateX(-200%);
}

.container.active .toggle-left {
  transform: translateX(0);
}

.toggle-right {
  right: 0;
  transform: translateX(0);
}

.container.active .toggle-right {
  transform: translateX(200%);
}
</style>

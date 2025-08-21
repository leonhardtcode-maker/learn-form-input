<script setup>
import { defineEmits, defineProps } from "vue";

const emit = defineEmits(["toggleShow", "submit", "login"]);
const emitShowLogin = () => emit("toggleShow", "showLogin");
const emitShowSignUp = () => emit("toggleShow", "showSignUp");
const emitSubmit = () => emit("submit", "submit");
const emitLogin = () => emit("login", "login");
const props = defineProps({
  showSignUp: Boolean,
  showLogin: Boolean,
});
const toggleSignUp = () => {
  if (props.showSignUp === false) {
    emitShowSignUp();
  } else if (props.showSignUp === true) {
    emitSubmit();
  }
};
</script>
<template>
  <div class="buttons-container">
    <button type="button" @click="toggleSignUp">
      <h1>Sign Up</h1>
    </button>
    <button type="button" @click="emitShowLogin"><h1>Login</h1></button>
  </div>
</template>
<style scoped>
.buttons-container {
  width: 100%;
  margin-top: clamp(0.5rem, 1vw, 1.4rem);
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
button {
  border: 0.1rem solid #007bff;
  background: transparent;
  border-radius: 0.5rem;
  width: 40%;
  border-radius: 1rem;
  padding: 0.1rem;
  transition-duration: 0.3s;
  font-size: clamp(0.3rem, 0.3vw, 1rem);
  color: #213547;
}
button:hover {
  background-color: #007bff;
  color: azure;
}
</style>

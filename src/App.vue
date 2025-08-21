<script setup>
import SignUpForm from "./components/SignUpForm.vue";
import LoginForm from "./components/LoginForm.vue";
import Button from "./components/Button.vue";
import { ref, reactive, provide } from "vue";

const showSignUp = ref(false);
const showLogin = ref(true);
const SignUp = reactive({
  email: "",
  fullname: "",
  password: "",
  role: "prospect",
  terms: false,
});
provide("SignUp", SignUp);
const formRef = ref(null); // ref ke child form

function toggleShow(componentName) {
  if (componentName === "showLogin") {
    showLogin.value = true;
    showSignUp.value = false;
  } else if (componentName === "showSignUp") {
    showLogin.value = false;
    showSignUp.value = true;
  }
}
function triggerSubmit() {
  if (formRef.value) {
    formRef.value.showSignUpAccount();
  }
}
</script>

<template>
  <div class="main-content">
    <div class="sign-up-container">
      <SignUpForm v-if="showSignUp" ref="formRef" />
      <LoginForm v-if="showLogin" />
      <Button
        @submit="triggerSubmit"
        @toggle-show="toggleShow"
        :showSignUp="showSignUp"
        :showLogin="showLogin"
      />
    </div>
    <div class="clean-window"></div>
  </div>
</template>

<style scoped>
.main-content {
  border-radius: 30px;
  height: 55vh;
  width: 40vw;
  max-width: 45rem;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 5%;
  padding: 20px;
  color: #213547;
  background-color: #ffffff;
  box-shadow: 0 0 50px rgba(0, 0, 0, 0.5);
}
.sign-up-container {
  height: 95%;
  border-radius: 20px;
  width: 100%;
  max-width: 20rem;
  padding: 0.5rem;
}
.clean-window {
  height: 95%;
  width: 60%;
  border-radius: 20px;
  background: url("./assets/pexels-tirachard-kumtanom.jpg") right bottom/cover
    no-repeat;
  background-attachment: fixed;
  border: 2px solid white;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
}
@media (max-width: 1024px) {
  .main-content {
    flex-direction: column;
  }
  .clean-window {
    width: 90%;
  }
}
</style>

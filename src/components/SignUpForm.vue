<script setup>
import { ref, computed, inject, defineExpose } from "vue";

const isShowError = ref(false);
const SignUp = inject("SignUp");

const toggleShowError = () => {
  isShowError.value = true;
};
const isShortPassword = computed(() => SignUp.password.length < 6);
const showSignUpAccount = () => {
  console.log(`Email: ${SignUp.email}`);
  console.log(`Full Name: ${SignUp.fullname}`);
  console.log(`Password: ${SignUp.password}`);
  console.log(`Role: ${SignUp.role}`);
};
defineExpose({ showSignUpAccount });
</script>

<template>
  <div class="form-container">
    <h1>Sign Up</h1>
    <form action="" class="forms" @submit.prevent="showSignUpAccount">
      <div class="form-group">
        <label for="email">EMAIL</label>
        <input
          type="text"
          name="email"
          id="email"
          v-model="SignUp.email"
          class="forms-control"
        />
      </div>
      <div class="form-group">
        <label for="fullname">FULL NAME</label>
        <input
          type="text"
          name="fullname"
          id="fullname"
          v-model="SignUp.fullname"
          class="forms-control"
        />
      </div>
      <div class="form-group">
        <label for="password">PASSWORD</label>
        <input
          type="password"
          name="password"
          id="password"
          v-model="SignUp.password"
          class="forms-control"
          @keydown="toggleShowError"
        />
        <div v-if="isShowError && isShortPassword" class="password-error">
          Password must be atleast 6 characters long
        </div>
      </div>
      <div class="form-group">
        <label for="role">ROLE</label>
        <select
          name="role"
          id="role"
          v-model="SignUp.role"
          class="forms-control"
        >
          <option value="member">Member</option>
          <option value="prospect">Prospect</option>
        </select>
      </div>
      <div class="terms-form">
        <input
          type="checkbox"
          id="terms"
          name="terms"
          v-model="SignUp.terms"
          required
        />
        <label for="terms">I Agree to the Terms and Conditions</label>
      </div>
    </form>
  </div>
  <!-- <p>{{ SignUp.role }}</p> -->
</template>

<style scoped>
h1 {
  font-size: clamp(0.6rem, 1.4vw, 1.5rem);
  margin-bottom: clamp(0.6rem, 1vw, 2rem);
}
label {
  font-size: clamp(0.4rem, 0.7vw, 1rem);
}
.forms {
  display: flex;
  flex-direction: column;
  align-items: start;
  gap: 0.5rem;
  font-weight: bold;
  color: #213547;
}
.form-group {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: start;
  gap: 0.5rem;
}
.form-group input,
select {
  color: #213547;
}
.forms-control {
  width: 100%;
  border: none;
  border-bottom: 2px solid #213547;
  outline: none;
  background: transparent;
  font-size: clamp(0.6rem, 0.9vw, 1rem);
  transition: border-color 0.2s ease;
}
.forms-control:focus {
  border-bottom: 2px solid #007bff;
}
.terms-form {
  margin-top: 0.5rem;
  display: flex;
  align-items: center;
  font-weight: normal;
}
.terms-form input[type="checkbox"] {
  width: 2vw;
  max-width: 2rem;
  margin-top: 0.4vw;
}
.password-error {
  line-height: 1;
  font-size: clamp(0.4rem, 0.7vw, 1rem);
  color: red;
}
</style>

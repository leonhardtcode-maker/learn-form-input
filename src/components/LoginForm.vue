<script setup>
import { reactive } from "vue";
const Login = reactive({
  email: "",
  password: "",
});
</script>

<template>
  <div class="form-container">
    <h1>Login</h1>
    <form action="" class="forms">
      <div class="form-group">
        <label for="email"><h2>EMAIL</h2></label>
        <input
          type="text"
          name="email"
          id="email"
          v-model="Login.email"
          class="forms-control"
        />
      </div>
      <div class="form-group">
        <label for="password"><h2>PASSWORD</h2></label>
        <input
          type="password"
          name="password"
          id="password"
          v-model="Login.password"
          class="forms-control"
        />
      </div>
      <div class="bottom-section">
        <form action="" class="remember-me">
          <input type="checkbox" id="remember-me" name="remember-me" />
          <label for="remember-me">Remember Me</label>
        </form>
        <a href="">Forgot Password?</a>
      </div>
    </form>
  </div>
</template>

<style scoped>
h1 {
  font-size: clamp(0.8rem, 1.4vw, 1.5rem);
  margin-bottom: clamp(0.6rem, 1vw, 2rem);
}
.forms {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  font-weight: bold;
  font-size: clamp(0.3rem, 0.5vw, 0.8rem);
  color: #213547;
}
.form-group {
  display: flex;
  flex-direction: column;
  align-items: start;
  font-weight: bold;
}
.form-group input {
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
.bottom-section {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: clamp(0.4rem, 0.7vw, 1rem);
  font-weight: normal;
}
.remember-me {
  display: flex;
  align-items: center;
}
.remember-me input[type="checkbox"] {
  width: 2vw;
  max-width: 2rem;
  margin-top: 0.35vw;
}
a:link,
a:visited,
a:link:active,
a:visited:active {
  color: #333;
  text-decoration: none;
}
</style>

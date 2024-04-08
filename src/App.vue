<script setup>
import { ref, reactive } from "vue";

const title = ref("Seu perfil");
const user = reactive({
  name: "",
  email: "",
  password: "",
  confirmPassword: "",
  birthDate: "",
  adress: "",
  city: [],
  states: [
    "AC",
    "AL",
    "AP",
    "AM",
    "BA",
    "CE",
    "DF",
    "ES",
    "GO",
    "MA",
    "MT",
    "MS",
    "MG",
    "PA",
    "PB",
    "PR",
    "PE",
    "PI",
    "RJ",
    "RN",
    "RS",
    "RO",
    "RR",
    "SC",
    "SP",
    "SE",
    "TO",
  ],
  hobbies: "",
  programmingLanguages: [
    "JavaScript",
    "Python",
    "C",
    "C++",
    "C#",
    "PHP",
    "TypeScript",
    "Ruby",
    "C",
    "Java",
    "Node.js",
    "Bash/Shell",
  ],
  biography: "",
});
</script>

<template>
  <div class="container">
    <h1 class="title">{{ title }}</h1>
    <form action="" class="form">
      <label for="name">Name</label>
      <input type="text" id="name" v-model="user.name">
      <label for="email">E-mail</label>
      <input type="email" name="email" id="email" v-model="email">
      <label for="password">Password</label>
      <input type="password" name="password" id="password" v-model="password">
      <label for="confirmPassword">Confirm password</label>
      <input type="password" name="confirmPassword" id="confirmPassword" v-model="confirmPassword">
      <label for="birthDate">Birth date</label>
      <input type="date" name="birthDate" id="birthDate" v-model="birthDate">
      <label for="adress">Adress</label>
      <input type="text" name="adress" id="adress" v-model="adress">
      <select name="" id="slctStates">
        <option v-for="item in user.states" :key="item" value="">
          {{ item }}
        </option>
      </select>
    </form>
  </div>
</template>

<style scoped></style>

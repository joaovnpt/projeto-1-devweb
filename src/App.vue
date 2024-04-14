<script setup>
import { ref, reactive } from "vue";

const title = ref("Your profile");
const user = reactive({
  name: "",
  email: "",
  password: "",
  confirmPassword: "",
  birthDate: "",
  adress: "",
  city: [],
  states: [
    "Your state",
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
      <label for="slctStates">State</label>
      <select name="slctStates" id="slctStates">
        <option v-for="item in user.states" :key="item" value="">
          {{ item }}
        </option>
      </select>
      <button type="submit" classs="submit-btn">Submit</button>
    </form>
  </div>
</template>

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Work+Sans:ital,wght@0,100..900;1,100..900&display=swap');

.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #DDDED9;
}

h1 {
  font-family: "Work sans";
  font-weight: bold;
}

.form {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 40px;
  background-color: rgb(250, 250, 250);
  border-radius: 30px;
  margin: 10px 0 10px 0;
}

input {
  height: 35px;
  width: 200px;
  border-radius: 10px;
  border-color: #BAB3AB;
  font-family: "Work sans";
  margin: 2px 10px 15px 5px; /*Top, right, bottom, left*/
  padding: 0px 0px 0px 10px;
}

label {
  display: flex;
  align-self:flex-start;
  font-family: "Work sans";
  margin: 0px 0px 0px 10px;
  font-size: 0.9rem;
}

select {
  width: 120px;
  height: 30px;
  border-radius: 5px;
  font-family: "Work sans";
  align-self: flex-start;
  margin: 2px 10px 15px 5px;
}
</style>

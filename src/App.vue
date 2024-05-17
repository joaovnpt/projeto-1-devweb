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

  ],
  language: "",
  biography: ""
});

function addLanguage() {
  if (user.language != 0) {
    user.programmingLanguages.push(user.language);
    user.language = "";
  }
}


function delLanguage(index) {
  user.programmingLanguages.splice(index, 1);
}
</script>

<template>
  <div class="container">
    <h1 class="title">{{ title }}</h1>
    <form action="" class="form">
      <label for="name">Name</label>
      <input type="text" id="name" v-model="user.name">
      <label for="email">E-mail</label>
      <input type="email" name="email" id="email" v-model="user.email">
      <label for="password">Password</label>
      <input type="password" name="password" id="password" v-model="user.password">
      <label for="confirmPassword">Confirm password</label>
      <input type="password" name="confirmPassword" id="confirmPassword" v-model="user.confirmPassword">
      <label for="birthDate">Birth date</label>
      <input type="date" name="birthDate" id="birthDate" v-model="user.birthDate">
      <label for="adress">Adress</label>
      <input type="text" name="adress" id="adress" v-model="user.adress">
      <label for="slctStates">State</label>
      <select name="slctStates" id="slctStates">
        <option v-for="item in user.states" :key="item" value="">
          {{ item }}
        </option>
      </select>
      <label for="hobbies">Hobbies</label>
      <input type="text" name="hobbies" id="hobbies" v-model="hobbies">
      <label for="programmingLanguages">Programming Languages</label>
      <div class="prog">
        <input type="text" name="programmingLanguages" id="programmingLanguages" v-model="user.language">
        <button type="button" @click="addLanguage()" class="add-programming-languages-btn">Add</button>
      </div>
      <ul>
        <li v-for="(language, index) in user.programmingLanguages" :key="language">{{ language }}
          <button class="del-button" @click="delLanguage(index)" type="button"><i class="fa fa-trash-o"></i></button>
        </li>
      </ul>
      <label for="biography">Biography</label>
      <textarea name="biography" id="biography" cols="30" rows="10" v-model="biography"></textarea>
      <button type="submit" class="submit-btn">Submit</button>
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
  align-items: flex-start;
  flex-direction: column;
  width: fit-content;
  padding: 40px;
  background-color: rgb(250, 250, 250);
  border-radius: 30px;
  margin: 10px 0 10px 0;
  box-shadow: 1px 1px 10px 1px rgba(0, 0, 0, 0.3);
  /* offset-x, offset-y, blur-radius, spread-radius */
}

input {
  height: 35px;
  width: 200px;
  border-radius: 10px;
  border-color: #BAB3AB;
  font-family: "Work sans";
  margin: 2px 10px 15px 5px;
  /*Top, right, bottom, left*/
  padding: 0px 0px 0px 10px;
}

label {
  display: flex;
  align-self: flex-start;
  font-family: "Work sans";
  margin: 0px 0px 0px 10px;
  font-size: 1rem;
}

select {
  width: 120px;
  height: 30px;
  border-radius: 5px;
  font-family: "Work sans";
  align-self: flex-start;
  margin: 2px 10px 15px 5px;
}

.prog {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: flex-start;
  align-self: flex-start;
}

#programmingLanguages {
  width: 148px;
  align-self: baseline;
  margin-right: 0;
}

.add-programming-languages-btn {
  margin: 2px 10px 0px 2px;
  width: 50px;
  height: 38px;
  border-color: #BAB3AB;
  cursor: pointer;
  transition: 100ms ease-out;
}

.add-programming-languages-btn:hover {
  transform: scale(1.05);
  transition: 100ms ease-out;
  border-color: green;
}

.add-programming-languages-btn:active {
  transform: scale(1.2);
  transition: 100ms;
}

.submit-btn {
  align-self: center;
  cursor: pointer;
}

ul {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  margin: 0px 0px 0px 15px;
  width: 100%;
  font-size: 0.9rem;
}

li {
  display: flex;
  justify-content: space-between;
  flex-direction: row;
  list-style: none;
  font-family: "Work sans";
  width: 100%;
  height: 30px;
  align-self: flex-start;
}

.del-button {
  margin: 0 30px;
  border: 0;
  height: fit-content;
  width: fit-content;
  cursor: pointer;
  align-self: end;
  font-size: 1rem;
  transition: 100ms ease-in-out
  
}

.del-button:hover {
  transform: scale(1.2);
  transition: 100ms ease-in-out;
  color: rgb(160, 0, 0);
}

textarea {
  border-radius: 10px;
  border-color: #BAB3AB;
  font-family: "Work sans";
  margin: 2px 10px 15px 5px;
  /*Top, right, bottom, left*/
  padding: 5px 0px 0px 5px;
}
</style>

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
  city: "",
  selectedState: "",
  hobbies: "",
  programmingLanguages: [],
  language: "",
  biography: "",
});

const states = [
  { uf: "AC", name: "Acre" },
  { uf: "AL", name: "Alagoas" },
  { uf: "AP", name: "Amapá" },
  { uf: "AM", name: "Amazonas" },
  { uf: "BA", name: "Bahia" },
  { uf: "CE", name: "Ceará" },
  { uf: "DF", name: "Distrito Federal" },
  { uf: "ES", name: "Espírito Santo" },
  { uf: "GO", name: "Goiás" },
  { uf: "MA", name: "Maranhão" },
  { uf: "MT", name: "Mato Grosso" },
  { uf: "MS", name: "Mato Grosso do Sul" },
  { uf: "MG", name: "Minas Gerais" },
  { uf: "PA", name: "Pará" },
  { uf: "PB", name: "Paraíba" },
  { uf: "PR", name: "Paraná" },
  { uf: "PE", name: "Pernambuco" },
  { uf: "PI", name: "Piauí" },
  { uf: "RJ", name: "Rio de Janeiro" },
  { uf: "RN", name: "Rio Grande do Norte" },
  { uf: "RS", name: "Rio Grande do Sul" },
  { uf: "RO", name: "Rondônia" },
  { uf: "RR", name: "Roraima" },
  { uf: "SC", name: "Santa Catarina" },
  { uf: "SP", name: "São Paulo" },
  { uf: "SE", name: "Sergipe" },
  { uf: "TO", name: "Tocantins" },
];

function addLanguage() {
  if (user.language != 0) {
    user.programmingLanguages.push(user.language);
    user.language = "";
  }
}

function delLanguage(index) {
  user.programmingLanguages.splice(index, 1);
}

let btnActivated = ref(false);

function showResult() {
  btnActivated.value = !btnActivated.value;
}
</script>

<template>
  <div class="container">
    <form action="" class="form">
      <h1 class="title">{{ title }}</h1>
      <div class="inputs">
        <label for="name">Name</label>
        <input type="text" id="name" v-model="user.name" />
        <label for="email">E-mail</label>
        <input type="email" name="email" id="email" v-model="user.email" />
        <label for="password">Password</label>
        <input type="password" name="password" id="password" v-model="user.password" />
        <label for="confirmPassword">Confirm password</label>
        <input type="password" name="confirmPassword" id="confirmPassword" v-model="user.confirmPassword" />
        <label for="birthDate">Birth date</label>
        <input type="date" name="birthDate" id="birthDate" v-model="user.birthDate" />
        <label for="adress">Adress</label>
        <input type="text" name="adress" id="adress" v-model="user.adress" />
        <label for="slctStates">State</label>
        <select name="slctStates" id="slctStates" v-model="user.selectedState">
          <option value="" disabled selected>Select a state</option>
          <option v-for="state of states" :key="state.uf">
            {{ state.name }}
          </option>
        </select>
        <label for="city">City:</label>
        <input type="text" name="city" id="city" v-model="user.city" />
        <label for="hobbies">Hobbies</label>
        <input type="text" name="hobbies" id="hobbies" v-model="user.hobbies" />
        <label for="programmingLanguages">Programming Languages</label>
        <div class="prog">
          <input type="text" name="programmingLanguages" id="programmingLanguages" v-model="user.language" />
          <button type="button" @click="addLanguage()" class="add-programming-languages-btn">
            Add
          </button>
        </div>
        <ul>
          <li v-for="(language, index) in user.programmingLanguages" :key="language">
            {{ language }}
            <button class="del-button" @click="delLanguage(index)" type="button">
              <i class="fa fa-trash-o"></i>
            </button>
          </li>
        </ul>
        <label for="biography">Biography</label>
        <textarea class="ls-textarea-autoresize" name="biography" id="biography" cols="25" rows="10"
          v-model="user.biography"></textarea>
      </div>
      <button @click="showResult()" type="button" class="show-result-bnt">
        Show result
      </button>
    </form>

    <div v-if="btnActivated" class="form" id="results-form">
      <div class="result-item">
        <p>Name:</p>
        {{ user.name }}
      </div>
      <div class="result-item">
        <p>E-mail:</p>
        {{ user.email }}
      </div>
      <div class="result-item">
        <p>Password:</p>
        {{ user.password }}
      </div>
      <div class="result-item">
        <p>Birth Date:</p>
        {{ user.birthDate }}
      </div>
      <div class="result-item">
        <p>Adress:</p>
        {{ user.adress }}
      </div>
      <div class="result-item">
        <p>State:</p>
        {{ user.selectedState }}
      </div>
      <div class="result-item">
        <p>City:</p>
        {{ user.city }}
      </div>
      <div class="result-item">
        <p>Hobbies:</p>
        {{ user.hobbies }}
      </div>
      <div class="result-item">
        <p>Programming Languages:</p>
        {{ user.programmingLanguages }}
      </div>
      <div class="result-item">
        <p>Biography:</p>
        <span class="bio">
          {{ user.biography }}
        </span>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Work+Sans:ital,wght@0,100..900;1,100..900&display=swap");

.container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  background-color: #ddded9;
}

.title {
  display: flex;
  margin: 0px 0px 30px 0px;
}

h1 {
  font-family: "Work sans";
  font-weight: bold;
}

.form {
  font-family: "Work sans";
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: fit-content;
  width: 350px;
  padding: 40px;
  background-color: rgb(250, 250, 250);
  border-radius: 30px;
  margin: 10px 50px 10px 50px;
  box-shadow: 1px 1px 10px 1px rgba(0, 0, 0, 0.3);
  /* offset-x, offset-y, blur-radius, spread-radius */
}

#results-form {
  display: flex;
  align-items: flex-start;
}

.inputs {
  display: flex;
  flex-direction: column;
  align-items: center;
}

input {
  height: 35px;
  width: 200px;
  border-radius: 10px;
  border-color: #d3cdc7;
  font-family: "Work sans";
  margin: 2px 10px 15px 5px;
  /*Top, right, bottom, left*/
  padding: 0px 0px 0px 10px;
}

input:hover {
  border-color: #b1a89f;
}

label {
  display: flex;
  align-self: flex-start;
  font-family: "Work sans";
  margin: 0px 0px 0px 13px;
  font-size: 1rem;
}

select {
  width: 120px;
  height: 30px;
  border-radius: 5px;
  background-color: #eceae8;
  font-family: "Work sans";
  align-self: flex-start;
  margin: 2px 10px 15px 13px;
}

select:hover {
  background-color: #e6e0db;
} 

.prog {
  display: flex;
  flex-direction: row;
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
  background-color: #eceae8; 
  border-color: #bab3ab;
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

.show-result-bnt {
  align-self: center;
  cursor: pointer;
  transition: 150ms ease-out;
  background-color: #5783db;
  color: white;
  width: 120px;
  height: 40px;
  border-color: rgb(146, 146, 146);
}

.show-result-bnt:hover {
  background-color: #4f79cc;
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
  transition: 100ms ease-in-out;
}

.del-button:hover {
  transform: scale(1.2);
  transition: 100ms ease-in-out;
  color: rgb(160, 0, 0);
}

textarea {
  border-radius: 10px;
  border-color: #bab3ab;
  font-family: "Work sans";
  margin: 2px 10px 15px 10px;
  /*Top, right, bottom, left*/
  padding: 5px 0px 0px 5px;
  resize: none;
}

#results-form>p {
  margin: 10px 0 0 0;
}

.result-item {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin: 5px 0 5px 0;
}

.result-item p {
  margin-right: 0.3em;
}

.bio {
  word-break: break-all;  
}
</style>

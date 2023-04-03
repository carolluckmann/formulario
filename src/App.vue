<script setup>
import { ref } from 'vue'
const name = ref('')
const email = ref('')
const password = ref('')
const dataNasc = ref('00/00/0000')
const endereco = ref('')
const cidade = ref('')
const hobbies = ref('')
const lingProg = ref('')
const bio = ref('')
const mostrarDiv = ref(false)
</script>

<template>
  <form @submit.prevent="mostrarDiv = !mostrarDiv">
    <div class="info">
      <label>Nome:</label>
      <input type="text" v-model="name" placeholder="Digite seu nome" minlength="3" maxlength="20" required/>
      <p>
        Email:
        <input type="email" v-model="email" placeholder="Digite seu email" required/>
      </p>
      <p>
        Senha:
        <input type="password" v-model="password" placeholder="Digite sua senha" required/>
      </p>
      <p>
        Confirme sua senha
        <input type="password" v-model="password" placeholder="Confirme sua senha" required/>
      </p>
      <p>
        Data de nascimento
        <input type="date" v-model="dataNasc" required> 
      </p>
      <p>
        Endereço
        <input type="text" v-model="endereco" placeholder="Digite seu endereço" />
      </p>
      <p>
        Cidade
        <input type="string" v-model="cidade" placeholder="Digite sua cidade" />
      </p>
      <p>
        <label for="estado">Informe seu estado</label>
        <select v-model="estado">
          <option value="AC">AC</option>
          <option value="AL">AL</option>
          <option value="AP">AP</option>
          <option value="AM">AM</option>
          <option value="BA">BA</option>
          <option value="CE">CE</option>
          <option value="DF">DF</option>
          <option value="ES">ES</option>
          <option value="GO">GO</option>
          <option value="MA">MA</option>
          <option value="MT">MT</option>
          <option value="MS">MS</option>
          <option value="MG">MG</option>
          <option value="PA">PA</option>
          <option value="PB">PB</option>
          <option value="PR">PR</option>
          <option value="PE">PE</option>
          <option value="PI">PI</option>
          <option value="RJ">RJ</option>
          <option value="RN">RN</option>
          <option value="RS">RS</option>
          <option value="RO">RO</option>
          <option value="RR">RR</option>
          <option value="SC">SC</option>
          <option value="SP">SP</option>
          <option value="SE">SE</option>
          <option value="TO">TO</option>
        </select>
      </p>
      <p>
        Hobbies
        <input type="text" v-model="hobbies" placeholder="Digite seus hobbies" maxlength="100">
      </p>
      <p>
        Linguagens de Programação 
        <input type="text" v-model="lingProg" placeholder="Digite quais linguagens você domina">
      </p>
      <p>
        Biografia
        <input type="text" v-model="bio" placeholder="Fale sobre você" minlength="200">
      </p>
      <button type="submit">Enviar</button>
    </div>
  </form>
  <div v-if="mostrarDiv">
    <p>Dados enviados com sucesso!</p>
    <p>Nome: {{ name }}</p>
    <p>Email: {{ email }}</p>
    <p>Data de nascimento: {{ dataNasc }}</p>
    <p>Endereço: {{ endereco }}</p>
    <p>Cidade: {{ cidade }}</p>
    <p>Estado: {{ estado }}</p>
    <p>Hobbies: {{ hobbies }}</p>
    <p>Linguagens de programação: {{ lingProg }}</p>
    <p>Biografia: {{ bio }}</p>
  </div>
</template>

<style scoped>
</style>

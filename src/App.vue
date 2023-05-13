<script setup>
import { ref } from 'vue'
const name = ref('')
const email = ref('')
const password = ref('')
const passwordConf = ref('')
const dataNasc = ref('00/00/0000')
const endereco = ref('')
const cidade = ref('')
const estado = ref('')
const estadoDesc = ref('')
const hobbies = ref('')
const lingProg = ref([])
const bio = ref('')
const imagem = ref('')
const msgError = ref('')
const mostrarDiv = ref(false)

function validaSenha() {
  atualizaEstado();
  if (password.value === passwordConf.value) {
    msgError.value = ''
    return true
  } else {
    msgError.value = 'As senhas não conferem'
    return false
  }
}

function atualizaEstado(){
switch (estado.value) {
  case 'AC':
    estadoDesc.value = 'Acre'
    break
  case 'AL':
    estadoDesc.value = 'Alagoas'
    break
  case 'AP':
    estadoDesc.value = 'Amapá'
    break
  case 'AM':
    estadoDesc.value = 'Amazonas'
    break
  case 'BA':
    estadoDesc.value = 'Bahia'
    break
  case 'CE':
    estadoDesc.value = 'Ceará'
    break
  case 'DF':
    estadoDesc.value = 'Distrito Federal'
    break
  case 'ES':
    estadoDesc.value = 'Espírito Santo'
    break
  case 'GO':
    estadoDesc.value = 'Goiás'
    break
  case 'MA':
    estadoDesc.value = 'Maranhão'
    break
  case 'MT':
    estadoDesc.value = 'Mato Grosso'
    break
  case 'MS':
    estadoDesc.value = 'Mato Grosso do Sul'
    break
  case 'MG':
    estadoDesc.value = 'Minas Gerais'
    break
  case 'PA':
    estadoDesc.value = 'Pará'
    break
  case 'PB':
    estadoDesc.value = 'Paraíba'
    break
  case 'PR':
    estadoDesc.value = 'Paraná'
    break
  case 'PE':
    estadoDesc.value = 'Pernambuco'
    break
  case 'PI':
    estadoDesc.value = 'Piauí'
    break
  case 'RJ':
    estadoDesc.value = 'Rio de Janeiro'
    break
  case 'RN':
    estadoDesc.value = 'Rio Grande do Norte'
    break
  case 'RS':
    estadoDesc.value = 'Rio Grande do Sul'
    break
  case 'RO':
    estadoDesc.value = 'Rondônia'
    break
  case 'RR':
    estadoDesc.value = 'Roraima'
    break
  case 'SC':
    estadoDesc.value = 'Santa Catarina'
    break
  case 'SP':
    estadoDesc.value = 'São Paulo'
    break
  case 'SE':
    estadoDesc.value = 'Sergipe'
    break
  case 'TO':
    estadoDesc.value = 'Tocantins'
    break
}
}

function handleFileUpload(e) {
  const target = e.target
  if (target && target.files) {
    const file = target.files[0]
    console.log(file)
    imagem.value = URL.createObjectURL(file)
  }
}
</script>

<template>
  <form @submit.prevent="mostrarDiv = validaSenha()">
    <div class="info">
      <h1 class="title">Formulário</h1>
      <p>
      <h3>Escolha sua foto de perfil:</h3>
        <input
          type="file"
          id="imagem"
          @change="handleFileUpload($event)"
        />
      </p>
      <label>Nome:</label>
      <input
        type="text"
        v-model="name"
        v-on:keypress="mostrarDiv = false"
        placeholder="Digite seu nome"
        minlength="3"
        maxlength="20"
        required
      />
      <p>
        <label>Email:</label>
        <input type="email" v-model="email" placeholder="Digite seu email" required />
      </p>
      <p>
        <label>Senha:</label>
        <input type="password" v-model="password" placeholder="Digite sua senha" required />
      </p>
      <p>
        <label>Confirme sua senha:</label>
        <input type="password" v-model="passwordConf" placeholder="Confirme sua senha" required />
      </p>
      <p>
        <label>Data de nascimento:</label>
        <input type="date" v-model="dataNasc" required />
      </p>
      <p>
        <label>Endereço:</label>
        <input type="text" v-model="endereco" placeholder="Digite seu endereço" />
      </p>
      <p>
        <label>Cidade:</label>
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
        <label>Hobbies:</label>
        <textarea
          type="text"
          v-model="hobbies"
          placeholder="Digite seus hobbies"
          maxlength="100"
        ></textarea>
      </p>
      <p>
        <label>Linguagens de Programação: </label>
         <input type="checkbox" v-model="lingProg" value="JavaScript" /> JavaScript
      <input type="checkbox" v-model="lingProg" value="PHP" /> PHP
      <input type="checkbox" v-model="lingProg" value="C++" /> C++
      <input type="checkbox" v-model="lingProg" value="SQL" /> SQL
      <input type="checkbox" v-model="lingProg" value="Python" /> Python
      </p>
      <p>
        <label>Biografia:</label>
        <textarea
          type="text"
          v-model="bio"
          placeholder="Fale sobre você"
          maxlength="200"
        ></textarea>
      </p>
      <button class="enviar" type="submit">Enviar</button>
    </div>
    <p class="error">{{ msgError }}</p>
  </form>
  <div class="mostraDiv" v-if="mostrarDiv">
    <p class="confirma">Dados enviados com sucesso!</p>
    <div class="img_perfil">
      <img :src="imagem" alt="" />
    </div>
    <p>Nome: {{ name }}</p>
    <p>Email: {{ email }}</p>
    <p>Data de nascimento: {{ dataNasc }}</p>
    <p>Endereço: {{ endereco }}</p>
    <p>Cidade: {{ cidade }}</p>
    <p>Estado: {{ estadoDesc }}</p>
    <p>Hobbies: {{ hobbies }}</p>
    <p>Linguagens de programação: {{ lingProg }}</p>
    <p>Biografia: {{ bio }}</p>
  </div>
</template>

<style scoped>

input{
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 8px;
  margin-bottom: 16px;
  margin-left: 5px;
}
textarea{
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 8px;
  margin-left: 5px;
}

select{
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 8px;
  margin-bottom: 16px;
  margin-left: 5px;
}
.info {
  background-color: rgb(250, 116, 174);
  padding: 20px 30px;
  color: rgb(224, 224, 224);
  border-radius: 10px;
}
h1 {
  color: white;
  font-weight: bold;
  font-size: 1.5em;
}
.error {
  color: red;
  font-weight: bold;
  font-size: 1.5em;
}
.mostraDiv {
  background-color: rgb(250, 116, 174);
  padding: 20px 30px;
  margin-left: 30px;
  color: rgb(183, 210, 219);
  border-radius: 10px;
}
.confirma {
  color: green;
  font-weight: bold;
  font-size: 1.5em;
}
.title {
  color: white;
  text-align: center;
  font-weight: bold;
  font-size: 2.5em;
  margin-bottom: 2px;
}

.enviar{
  border-radius: 5px;
  border-color: black;
  color: black;
  background-color: rgb(250, 116, 174);
  font-weight: bold;
  font-size: 1.5em;
  margin-top: 15px;
}

.enviar:hover{
  background-color: rgb(255, 149, 195);
}

.img_perfil {
  width: '80%';
  display: flex;
  justify-content: center;
}

.img_perfil {
  width: 200px;
  height: 200px;
  border-radius: 50%;
}
</style>

<template>
  <div class="wrapper">
    <div class="container">
      <h2>Passo 4</h2>
      <form @submit.prevent="submitForm" class="inputs">
        <div>
          <h3>Revisão suas informações</h3>
          <div class="form-group">
            <label for="email">Email:</label>
            <input
              type="email"
              v-model="localFormData.email"
              id="email"
              class="form-input"
            />
          </div>
          <div class="form-group">
            <label for="registrationType">Tipo de Cadastro:</label>
            <input
              type="text"
              v-model="localFormData.registrationType"
              id="registrationType"
              class="form-input"
              disabled
            />
          </div>
          <div v-if="localFormData.registrationType === 'PF'">
            <div class="form-group">
              <label for="name">Nome:</label>
              <input
                type="text"
                v-model="localFormData.name"
                id="name"
                class="form-input"
              />
            </div>
            <div class="form-group">
              <label for="cpf">CPF:</label>
              <input
                type="text"
                v-model="localFormData.cpf"
                id="cpf"
                class="form-input"
              />
            </div>
            <div class="form-group">
              <label for="dob">Data de Nascimento:</label>
              <input
                type="date"
                v-model="localFormData.dob"
                id="dob"
                class="form-input"
              />
            </div>
            <div class="form-group">
              <label for="phone">Telefone:</label>
              <input
                type="text"
                v-model="localFormData.phone"
                id="phone"
                class="form-input"
              />
            </div>
          </div>
          <div v-else>
            <div class="form-group">
              <label for="companyName">Razão Social:</label>
              <input
                type="text"
                v-model="localFormData.companyName"
                id="companyName"
                class="form-input"
              />
            </div>
            <div class="form-group">
              <label for="cnpj">CNPJ:</label>
              <input
                type="text"
                v-model="localFormData.cnpj"
                id="cnpj"
                class="form-input"
              />
            </div>
            <div class="form-group">
              <label for="establishmentDate"
                >Data de Abertura da Empresa:</label
              >
              <input
                type="date"
                v-model="localFormData.establishmentDate"
                id="establishmentDate"
                class="form-input"
              />
            </div>
            <div class="form-group">
              <label for="companyPhone">Telefone:</label>
              <input
                type="text"
                v-model="localFormData.companyPhone"
                id="companyPhone"
                class="form-input"
              />
            </div>
          </div>
          <div class="form-group">
            <label for="password">Senha:</label>
            <input
              type="password"
              v-model="localFormData.password"
              id="password"
              class="form-input"
            />
          </div>
          <input type="hidden" />
        </div>
        <div class="buttons">
          <button type="button" @click="$emit('previous-step')">Voltar</button>
          <button type="button" class="btn1" @click="$emit('handle-api')">
            Cadastrar
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "RegistrationStep4",
  props: ["formData"],
  data() {
    return {
      localFormData: { ...this.formData },
    };
  },
  methods: {
    submitForm() {
      this.$emit("submit", this.localFormData);
    },
  },
};
</script>

<style scoped>
.wrapper {
  display: flex;
  justify-content: center;
}
.container {
  width: 220px;
}
.steps {
  font-size: 12px;
}
.steps span {
  color: #f19806;
}
.inputs {
  width: 94%;
}
.inputs label {
  width: 100%;
  display: block;
  font-size: 12px;
}
.inputs input {
  width: 100%;
  border-radius: 5px;
  border: 1px solid #000000;
  padding: 5px;
}
.inputs div {
  margin-bottom: 10px;
}
.radios {
  display: flex;
  margin: 20px 0px;
  font-size: 12px;
}
.buttons {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
}
.buttons .btn1 {
  background-color: #f19806;
  color: #ffffff;
  text-align: center;
  padding: 5px 10px;
  border: none;
  border-radius: 5px;
}
button[type="button"] {
  border: 1px solid #f19806;
  background: none;
  color: #f19806;
  text-align: center;
  padding: 5px 10px;
  border-radius: 5px;
}
</style>

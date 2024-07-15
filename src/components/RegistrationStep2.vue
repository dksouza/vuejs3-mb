<template>
  <div class="wrapper">
    <div class="container">
      <div class="steps">Etapa <span>2</span> de 4</div>

      <form @submit.prevent="nextStep">
        <div v-if="registrationType === 'PF'" class="inputs">
          <h2>Pessoa física</h2>
          <div>
            <label for="name">Nome:</label>
            <input type="text" v-model="name" required />
          </div>
          <div>
            <label for="cpf">CPF:</label>
            <input type="text" v-model="cpf" required />
          </div>
          <div>
            <label for="dob">Data de nascimento:</label>
            <input type="date" v-model="dob" required />
          </div>
          <div>
            <label for="phone">Número de telefone:</label>
            <input type="text" v-model="phone" required />
          </div>
        </div>
        <div v-else class="inputs">
          <h2>Pessoa jurídica</h2>
          <div>
            <label for="companyName">Razão social:</label>
            <input type="text" v-model="companyName" required />
          </div>
          <div>
            <label for="cnpj">CNPJ:</label>
            <input type="text" v-model="cnpj" required />
          </div>
          <div>
            <label for="establishmentDate">Data de abertura da empresa:</label>
            <input type="date" v-model="establishmentDate" required />
          </div>
          <div>
            <label for="companyPhone">Telefone:</label>
            <input type="text" v-model="companyPhone" required />
          </div>
        </div>
        <div class="buttons">
          <button type="button" @click="$emit('previous-step')">Voltar</button>
          <button type="submit">Continuar</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  props: ["registrationType"],
  data() {
    return {
      name: "",
      cpf: "",
      dob: "",
      phone: "",
      companyName: "",
      cnpj: "",
      establishmentDate: "",
      companyPhone: "",
    };
  },
  methods: {
    nextStep() {
      if (this.registrationType === "PF") {
        if (this.name && this.cpf && this.dob && this.phone) {
          this.$emit("next-step", {
            name: this.name,
            cpf: this.cpf,
            dob: this.dob,
            phone: this.phone,
          });
        } else {
          alert("Por favor, preencha todos os campos.");
        }
      } else {
        if (
          this.companyName &&
          this.cnpj &&
          this.establishmentDate &&
          this.companyPhone
        ) {
          this.$emit("next-step", {
            companyName: this.companyName,
            cnpj: this.cnpj,
            establishmentDate: this.establishmentDate,
            companyPhone: this.companyPhone,
          });
        } else {
          alert("Por favor, preencha todos os campos.");
        }
      }
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
button[type="submit"] {
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

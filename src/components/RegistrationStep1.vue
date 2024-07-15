<template>
  <div class="wrapper">
    <div class="container">
      <div class="steps">Etapa <span>1</span> de 4</div>
      <h2>Seja bem vindo(a)</h2>
      <form @submit.prevent="nextStep">
        <div class="inputs">
          <label for="email">Endereço de e-mail:</label>
          <input type="email" v-model="email" required />
        </div>
        <div class="radios">
          <div>
            <input type="radio" id="pf" value="PF" v-model="registrationType" />
            <label for="pf">Pessoa Física</label>
          </div>
          <div>
            <input type="radio" id="pj" value="PJ" v-model="registrationType" />
            <label for="pj">Pessoa Jurídica</label>
          </div>
        </div>
        <button type="submit" class="submit">Continuar</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      registrationType: "",
    };
  },
  methods: {
    nextStep() {
      if (this.email && this.registrationType) {
        this.$emit("next-step", {
          email: this.email,
          registrationType: this.registrationType,
        });
      } else {
        alert("Por favor, preencha todos os campos.");
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
  width: 100%;
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
.radios {
  display: flex;
  margin: 20px 0px;
  font-size: 12px;
}
.submit {
  background-color: #f19806;
  color: #ffffff;
  text-align: center;
  padding: 5px 20px;
  width: 100%;
  border: none;
  border-radius: 5px;
}
</style>

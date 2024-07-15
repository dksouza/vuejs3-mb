<template>
  <div class="wrapper">
    <div class="container">
      <div class="steps">Etapa <span>3</span> de 4</div>
      <h2>Passo 3</h2>
      <form @submit.prevent="nextStep" class="inputs">
        <div>
          <label for="password">Senha de acesso:</label>
          <input type="password" v-model="password" required />
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
  data() {
    return {
      password: "",
    };
  },
  methods: {
    nextStep() {
      if (this.password) {
        this.$emit("next-step", { password: this.password });
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

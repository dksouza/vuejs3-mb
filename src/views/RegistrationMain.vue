<template>
  <div>
    <component
      :is="currentStepComponent"
      :formData="formData"
      :registrationType="formData.registrationType"
      @next-step="handleNextStep"
      @previous-step="handlePreviousStep"
      @handle-api="handleApi"
    >
    </component>
  </div>
</template>

<script>
import RegistrationStep1 from "../components/RegistrationStep1.vue";
import RegistrationStep2 from "../components/RegistrationStep2.vue";
import RegistrationStep3 from "../components/RegistrationStep3.vue";
import RegistrationStep4 from "../components/RegistrationStep4.vue";

export default {
  name: "RegistrationMain",
  components: {
    RegistrationStep1,
    RegistrationStep2,
    RegistrationStep3,
    RegistrationStep4,
  },
  data() {
    return {
      currentStep: 1,
      formData: {
        email: "",
        registrationType: "",
        name: "",
        cpf: "",
        dob: "",
        phone: "",
        companyName: "",
        cnpj: "",
        establishmentDate: "",
        companyPhone: "",
        password: "",
      },
    };
  },
  computed: {
    currentStepComponent() {
      return `RegistrationStep${this.currentStep}`;
    },
  },
  methods: {
    handleNextStep(data) {
      Object.assign(this.formData, data);
      if (this.currentStep < 4) {
        this.currentStep += 1;
      }
    },
    handlePreviousStep() {
      if (this.currentStep > 1) {
        this.currentStep -= 1;
      }
    },
    handleApi() {
      if (this.currentStep === 4) {
        alert("Cadastro realizado com sucesso!");
      }
    },
  },
};
</script>

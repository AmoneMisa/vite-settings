<template>
  <vee-form class="form" @submit="$emit('submit:form', sendFormData())">
    <div class="form__item">
      <vee-field type="text" name="name" placeholder="Your name" :rules="validateName" class="input" @input="e => getInputData(e.target)"/>
      <div class="form__error">
        <error-message name="name" class="error-msg" />
      </div>
    </div>
    <div class="form__item">
      <vee-field type="email" name="email" placeholder="Email" :rules="validateEmail" class="input" @input="e => getInputData(e.target)"/>
      <div class="form__error">
        <error-message name="email" class="error-msg" />
      </div>
    </div>
    <div class="form__item">
      <vee-field type="tel" name="phone" placeholder="Phone" :rules="validatePhone" class="input" @input="e => getInputData(e.target)"/>
      <div class="form__error">
        <error-message name="phone" class="error-msg" />
      </div>
    </div>
    <div class="form__item">
      <custom-select placeholder="Country" :options="countries" name="country" @input="e => getInputData(e.target)"/>
    </div>
    <div class="form__item">
      <custom-input placeholder="Delivery address" type="text" name="address" @input="e => getInputData(e.target)" />
    </div>
    <div class="form__item">
      <custom-input placeholder="Agreement with our policy" type="checkbox" name="agreement" @input="e => getInputData(e.target)" required>
        Check it, if you agree with our policy
      </custom-input>
    </div>
    <custom-button type="submit" class="form__button">Create order</custom-button>
  </vee-form>
</template>

<script>
import {Form, Field, ErrorMessage} from "vee-validate";
import Input from "./components/Input.vue";
import Select from "./components/Select.vue";
import Button from "./components/Button.vue";

export default {
  name: "CreateOrderForm",
  components: {
    VeeForm: Form,
    VeeField: Field,
    ErrorMessage,
    CustomInput: Input,
    CustomSelect: Select,
    CustomButton: Button,
  },
  data() {
    return {
      formData: {},
      countries: [{
        name: "Ukraine",
        id: 1,
        value: "Ukraine"
      }, {
        name: "Turkey",
        id: 2,
        value: "Turkey"
      }, {
        name: "EU",
        id: 3,
        value: "EU"
      }],
    }
  },
  methods: {
    sendFormData() {
      console.log(JSON.stringify(this.formData));
    },
    getInputData(input) {
      this.formData[input.name] = input.value;
    },
    validateEmail(value) {
      if (!value) {
        return 'This field is required';
      }

      const regex = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
      if (!regex.test(value)) {
        return 'This field must be a valid email';
      }

      return true;
    },
    validatePhone(value) {
      if (!value) {
        return 'This field is required';
      }

      const regex = /^[+]?[(]?[0-9]{3}[)]?[-\s.]?[0-9]{3}[-\s.]?[0-9]{4,6}$/im;
      if (!regex.test(value)) {
        return 'This field must be a valid phone';
      }

      return true;
    },
    validateName(value) {
      if (!value) {
        return 'This field is required';
      }

      const regex = /[A-Za-zА-Яа-я]/;
      if (!regex.test(value)) {
        return 'This field must be a valid text';
      }

      return true;
    }
  },
  emits: ["submit:form"]
}
</script>

<style scoped>

</style>
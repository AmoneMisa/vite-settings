<template>
  <form class="form" @submit.prevent="e => $emit('submit:form', sendFormData(e.target))">
    <div class="form__item" v-for="input in inputs">
      <custom-input :placeholder="input.placeholder" :type="input.type" :name="input.name" v-if="!(input.type === 'select')" :required="input.required || false" @input="e => getInputData(e.target)">
        {{ input.text }}
      </custom-input>
      <custom-select :placeholder="input.placeholder" :options="input.options" :name="input.name" v-if="input.type === 'select'" :required="input.required || false"/>
    </div>
    <custom-button type="submit" class="form__button">{{ buttonMsg }}</custom-button>
  </form>
</template>

<script>
import Input from "./Input.vue";
import Select from "./Select.vue";
import Button from "./Button.vue";

export default {
  name: "Form",
  components: {
    CustomInput: Input,
    CustomSelect: Select,
    CustomButton: Button
  },
  props: {
    inputs: Array,
    buttonMsg: String,
  },
  data() {
    return {
      formData: {}
    }
  },
  methods: {
    getInputData(input) {
      this.formData[input.name] = input.value;
    },
    sendFormData() {
      let numberFormat = new Intl.NumberFormat('en-US', );

      this.formData.price = numberFormat.format(this.formData.price);
      return JSON.stringify(this.formData);
    }
  },
  emits: ["submit:form"]
}
</script>

<style lang="scss">
  .form {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    overflow: auto;
    height: 100%;
  }

  .form__item {
    &:not(:last-child) {
      margin-bottom: 10px;
    }
  }

  .form__error {
  }

  .error-msg {
    color: #8f1313;
    font-size: 11px;
  }
</style>
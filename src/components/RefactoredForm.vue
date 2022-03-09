<template>
  <ValidationObserver ref="observer" v-slot="{ handleSubmit }">
    <b-form @submit.prevent="handleSubmit(onSubmit)" @reset="resetForm">
      <BTextInputWithValidation
        rules="required|email"
        type="email"
        label="Email address:"
        name="Email"
        v-model="email"
        description="We'll never share your email with anyone else"
        placeholder="Enter email"
      />

      <BTextInputWithValidation
        rules="required"
        name="Password"
        vid="password"
        type="password"
        label="Password"
        v-model="password"
        description="We'll never share your password with anyone else"
        placeholder="Enter password"
      />

      <BTextInputWithValidation
        rules="required|confirmed:password"
        name="Password confirmation"
        type="password"
        label="Password confirmation"
        v-model="confirmation"
        description="We'll never share your password with anyone else"
        placeholder="Confirm password"
      />

      <BSelectWithValidation rules="required" label="Subject:" v-model="subject">
        <option value="null">None</option>
        <option value="S1">Subject 1</option>
        <option value="S2">Subject 2</option>
      </BSelectWithValidation>

      <BCheckboxesWithValidation v-model="choices" rules="required">
        <b-form-checkbox value="Coffee">Coffe</b-form-checkbox>
        <b-form-checkbox value="Tea">Tea</b-form-checkbox>
        <b-form-checkbox value="Soda">Soda</b-form-checkbox>
      </BCheckboxesWithValidation>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </ValidationObserver>
</template>

<script>
import { ValidationObserver } from "vee-validate";
import BTextInputWithValidation from "./inputs/BTextInputWithValidation";
import BSelectWithValidation from "./inputs/BSelectWithValidation";
import BCheckboxesWithValidation from "./inputs/CheckboxesWithValidation";

export default {
  name: "BootstrapForm",
  components: {
    ValidationObserver,
    BTextInputWithValidation,
    BSelectWithValidation,
    BCheckboxesWithValidation
  },
  data: () => ({
    email: "",
    password: "",
    confirmation: "",
    subject: "",
    choices: []
  }),
  watch: {
    subject(val) {
      console.log(val);
    }
  },
  methods: {
    onSubmit() {
      console.log("Form submitted yay!");
    },
    resetForm() {
      this.email = "";
      this.password = "";
      this.confirmation = "";
      this.subject = "";
      this.choices = [];
      requestAnimationFrame(() => {
        this.$refs.observer.reset();
      });
    }
  }
};
</script>

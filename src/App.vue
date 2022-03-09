<template>
  <b-container id="app">
    <BForm/>
    <!-- <RefactoredForm/> -->
  </b-container>
</template>

<script>
import Form from "./components/Form";
import RefactoredForm from "./components/RefactoredForm";

export default {
  name: "App",
  components: {
    BForm: Form,
    RefactoredForm
  }
};
</script>

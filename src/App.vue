<template>
  <div class="m-4">
    <ButtonSample />
    <DialogSample />
    <InputTextSample />
    <InputRadioSample />
  </div>
</template>

<script>
import ButtonSample from "./components/buttons/ButtonSample.vue";
import DialogSample from "./components/modals/DialogSample.vue";
import InputTextSample from "./components/forms/InputTextSample.vue";
import InputRadioSample from "./components/forms/InputRadioSample.vue";
export default {
  name: "App",
  components: {
    ButtonSample,
    DialogSample,
    InputTextSample,
    InputRadioSample,
  },
};
</script>
<style scoped>
div {
  margin: 32px;
}
</style>

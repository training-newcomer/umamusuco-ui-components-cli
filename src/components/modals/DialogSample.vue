<template>
  <div>
    <p class="mb-2 text-2xl">Dialogs</p>
    <div>
      <MyDialog :visible="dialogVisible" @backdrop-clicked="switchDialog">
        <template #title>
          <p class="font-bold">ダイアログ</p>
        </template>
        <template #body>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum nihil
          dolores harum cum cupiditate error, sequi iure? Ut sunt quisquam
          dolorem, eum, natus maiores officia quas autem error, optio
          voluptates!
        </template>
        <template #footer>
          <div class="flex justify-end">
            <SecondaryButton @click="switchDialog">close</SecondaryButton>
          </div>
        </template>
      </MyDialog>
    </div>
    <div class="mb-2">
      <PrimaryButton @click="switchDialog">open</PrimaryButton>
    </div>
  </div>
</template>

<script>
import { ref } from "@vue/composition-api";
import SecondaryButton from "../buttons/SecondaryButton.vue";
import PrimaryButton from "../buttons/PrimaryButton.vue";
import MyDialog from "./MyDialog.vue";

export default {
  name: "DialogSample",
  components: {
    PrimaryButton,
    SecondaryButton,
    MyDialog,
  },
  setup() {
    const dialogVisible = ref(false);
    const switchDialog = () => {
      dialogVisible.value = !dialogVisible.value;
    };
    return {
      dialogVisible,
      switchDialog,
    };
  },
};
</script>

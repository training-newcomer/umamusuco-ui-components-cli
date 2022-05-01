<template>
  <BaseButton :disabled="disabled" :class="buttonClass" @click="handleClick">
    <slot />
  </BaseButton>
</template>

<script>
import BaseButton from "./BaseButton.vue";
export default {
  name: "PrimaryButton",
  components: {
    BaseButton,
  },
  props: {
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleClick() {
      this.$emit("click");
    },
  },
  computed: {
    buttonClass() {
      return this.disabled
        ? "text-gray-400 bg-gray-100"
        : "text-white bg-gray-800";
    },
  },
};
</script>

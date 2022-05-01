<template>
  <div>
    <a
      v-if="$attrs.href"
      v-bind="$attrs"
      :disabled="disabled"
      class="inline-flex items-center justify-center px-2 no-underline rounded-md h-11"
      :class="linkButtonClass"
    >
      <slot />
    </a>
    <BaseButton
      v-else
      :disabled="disabled"
      :class="buttonClass"
      @click="handleClick"
    >
      <slot />
    </BaseButton>
  </div>
</template>

<script>
import BaseButton from "./BaseButton.vue";
export default {
  name: "SecondaryButton",
  components: {
    BaseButton,
  },
  inheritAttrs: false,
  props: {
    disabled: {
      type: Boolean,
      default: false,
    },
    link: {
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
    linkButtonClass() {
      return this.disabled
        ? "text-gray-400 bg-gray-100"
        : "text-gray-900 bg-gray-200";
    },
  },
};
</script>

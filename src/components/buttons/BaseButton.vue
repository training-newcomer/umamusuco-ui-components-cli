<template>
  <button class="px-2 rounded-md h-11" @click="handleClick">
    <slot />
  </button>
</template>

<script>
export default {
  name: "BaseButton",
  methods: {
    handleClick() {
      this.$emit("click");
    },
  },
};
</script>

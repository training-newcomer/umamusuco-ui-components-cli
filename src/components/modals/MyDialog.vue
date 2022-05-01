<template>
  <Teleport v-if="visible" to="body">
    <div
      v-bind="$attrs"
      class="fixed top-0 left-0 flex items-start justify-center w-screen h-screen overflow-y-scroll backdrop-filter backdrop-blur-md"
      @click.stop="clickBackDrop"
    >
      <section
        class="box-border max-w-screen-sm p-3 mx-2 my-16 bg-white shadow-xl rounded-20"
        @click.stop
      >
        <header>
          <div class="w-full text-center">
            <slot name="title"></slot>
          </div>
        </header>
        <div class="py-3">
          <slot name="body" />
        </div>
        <footer>
          <slot name="footer"></slot>
        </footer>
      </section>
    </div>
  </Teleport>
</template>

<script>
import { watchEffect } from "@vue/composition-api";
import Teleport from "vue2-teleport";

export default {
  name: "MyDialog",
  components: {
    Teleport,
  },
  props: {
    visible: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    clickBackDrop() {
      this.$emit("backdropClicked");
    },
  },

  setup(props) {
    watchEffect((onInvalidate) => {
      if (!props.visible) return;
      const overflow = document.documentElement.style.overflow;
      document.documentElement.style.overflow = "hidden";
      onInvalidate(() => {
        document.documentElement.style.overflow = overflow;
      });
    });
  },
};
</script>

<template>
  <div class="modal">
    <div class="overlay" @click="emit('closeModal')"></div>
    <div class="modal-card">
      <slot />
    </div>
  </div>
</template>

<script>
import { onBeforeUnmount } from "vue";
export default {
  setup(props, { emit }) {
    let onKeyDown = (event) => {
      console.log(event.key);
      if (event.key === "Escape") {
        emit("closeModal");
      }
    };
    window.addEventListener("keydown", onKeyDown);

    onBeforeUnmount(() => {
      window.removeEventListener("keydown", onKeyDown);
    });

    return {
      emit,
    };
  },
};
</script>

<style scoped>
</style>
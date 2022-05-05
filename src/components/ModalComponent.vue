<template>
  <!-- .self is an event modifier, the event is only triggered if is click on the background-overlay, not the childrens -->
  <div class="background-overlay" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <header>
        <a
          role="button"
          aria-label="Close Modal"
          class="close"
          @click="closeModal"
          >X</a
        >
      </header>
      <!-- Using slot with a default value -->
      <slot>default content</slot>

      <footer class="buttons">
        <!-- Named Slot -->
        <slot name="buttons"></slot>
      </footer>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalComponent",
  // Props can be used in this component as attributes
  // They are not required
  props: ["theme"],

  methods: {
    closeModal() {
      // Emit a custom event
      this.$emit("close");
    },
  },
};
</script>


<style scoped>
.background-overlay {
  position: fixed;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;

  width: 100%;
  height: 100%;

  display: flex;
  justify-content: center;
  align-items: center;

  background: rgba(0, 0, 0, 0.3);
}

.modal {
  width: 480px;
  max-width: 90%;

  padding: 1.5rem;
  margin: auto;

  background-color: #fff;

  border-radius: 10px;

  text-align: center;
}

.modal.sale {
  background-color: #47e27b;
  color: #fff;
}

header {
  display: flex;
  justify-content: end;
}

.close {
  cursor: pointer;
}

.buttons {
  margin-top: 1.5rem;

  display: flex;
  justify-content: space-around;
  align-items: center;
}

.button {
  padding: 1rem 1.15rem;

  color: #fff;
  text-decoration: none;

  background-color: #475ee2;

  border-radius: 10px;
}

.sale .button {
  background-color: transparent;

  border: 1px solid #fff;
}
</style>
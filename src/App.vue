<template>
  <main>
    <h1>{{ title }}</h1>

    <!-- Using the ref object to get the input as javascript -->
    <input type="text" ref="name" />
    <button @click="handleRefs">click me</button>

    <!-- Using a component -->
    <!-- Passing props to the component -->
    <!-- The @close is a custom event created in the ModalComponent -->
    <ModalComponent v-if="showModal" :theme="theme" @close="toggleModal">
      <h1>Hello There</h1>
      <p>You can pass an entire template to the component, using slots</p>

      <!-- Named Slot -->
      <template v-slot:buttons>
        <a href="" class="button">sign up</a>
        <a href="" class="button">more info</a>
      </template>
    </ModalComponent>

    <button @click="toggleModal">open modal</button>
  </main>
</template>

<script>
import ModalComponent from "./components/ModalComponent";
export default {
  name: "App",
  components: {
    ModalComponent,
  },
  data() {
    return {
      title: "Hello World!",
      header: "Header Title",
      text: "Testing props",
      theme: "sale",
      showModal: false,
    };
  },
  methods: {
    handleRefs() {
      // Using normal javascript to manipulate the input with refs
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
  },
};
</script>

<style>
main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  height: 100%;
}
</style>

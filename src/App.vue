<template>
  <h1>{{ title }}</h1>
  <br />
  <input type="text" ref="name" />
  <button @click="handleClick">Click Me</button>

  <teleport to="#modals" v-if="showModal">
    <Modal theme="dark" @close="toggleModal"> <!-- ada 2 theme dark dan sale -->
      <h1>Hello World</h1>
      <p>Grab your stuff for half price!</p>
      <template v-slot:links>
        <a href="">Sign Up Now</a> 
        <a href="">More info</a>
      </template>
    </Modal>
  </teleport>

  <br />

  <teleport to="#modals" v-if="showModal2">
    <Modal theme="sale" @close="toggleModal2">
      <h1>World Hello</h1>
      <p>Blablabla Blablabla</p>
      <template v-slot:links>
        <a href="">Click Me 1</a>
        <a href="">Click Me 2</a>
      </template>
    </Modal>
  </teleport>

  <br />

  <button @click="toggleModal2">Open Second Modal</button>
  <button @click.alt="toggleModal">Open Modal (alt)</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My First Vue App :)",
      header: "Sign Up for the Giveaway!",
      text: "Grab your stuff for half price!",
      showModal: false,
      showModal2: false
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active"); //adding class to ref
      this.$refs.name.focus(); //ref will be focused
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModal2(){
      this.showModal2 = !this.showModal2;
    }
  }
};
</script>

<style>
#app, #modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}

button{
  margin: 10px;
}
</style>

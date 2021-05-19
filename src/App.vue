<template>
  <h1>{{title}}</h1>
  <p>Welcome...</p>
  <teleport to=".modals" v-if="showModal">
    <label>
      <input type="text" ref="name">
      <button @click="handleClick">Click Me</button>
      <Modal theme="" @close="toggleModal">
        <h1>Sign Up Here!!!!</h1>
        <p>Hey Are You A Deaf Quickly DO IT!!</p>
        <template v-slot:links>
          <a href="#">Contact</a>
          <a href="#">More</a>
        </template>
      </Modal>
    </label>
  </teleport>

  <div v-if="showModalTwo">
    <label>
      <input type="text" ref="name">
      <button @click="handleClick">Click Me</button>
      <Modal theme="" @close="toggleModalTwo">
        <h1>This is modal 2!!!!</h1>
        <p>Never Live Happily!!</p>
        <template v-slot:links>
          <a href="#">Number</a>
          <a href="#">Block</a>
        </template>
      </Modal>
    </label>
  </div>

  <button @click="toggleModal"> Open Modal </button>
  <br>
  <button @click="toggleModalTwo"> Open Modal Two </button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: {Modal},
  data() {
    return {
      title: "My First Vue App",
      header: "Sign Up Here!!!!",
      text: "Hey Are You A Deaf Quickly DO IT!!",
      showModal: false,
      showModalTwo: false,
    }
  },
  methods: {
    handleClick() {
      console.log(this.title)
      console.log(this.$refs.name)
      this.$refs.name.classList.add("active")
      this.$refs.name.focus()
    },

    toggleModal() {
      this.showModal = !this.showModal
    },

    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  }
}
</script>

<style>
#app, .modals{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>

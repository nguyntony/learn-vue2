<template>
  <h1>{{ title }}</h1>
  <!-- <input type="text" ref="name" />
  <button @click="handleClick">click</button> -->
  <div v-if="showModal">
    <Modal
      :header="header"
      :text="text"
      :obj="{ content: `I'm inside of an obj` }"
      theme="sale"
      @close="toggleModal"
    />
  </div>
  <button @click="toggleModal">open modal</button>
  <div>
    <Tester
      header="hi we are passing a prop here."
      :one="one"
      :two="two"
      :three="three"
      :showSecret="showSecret"
      @press="toggleSecret"
    />
  </div>
</template>

<script>
import Modal from './components/Modal';
import Tester from './components/Tester';

export default {
  name: 'App',
  components: {
    Modal,
    Tester,
  },
  data() {
    return {
      title: 'my new title',
      header: 'sign up now!!!',
      text: `if you do then that's good!`,
      showModal: false,
      one: 'number1',
      two: 'number2',
      three: 'number3',
      showSecret: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add('active');
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleSecret() {
      this.showSecret = !this.showSecret;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  color: cornflowerblue;
}
</style>

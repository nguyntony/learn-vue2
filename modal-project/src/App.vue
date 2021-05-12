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
  <div>
    <h1>this section is about SLOTS</h1>
    <Slots>
      <p>hhi hih ihih</p>
      <template v-slot:links>
        <a href="#">login</a>
        <a href="#">more info</a>
      </template>
    </Slots>
  </div>
  <div v-if="showModal2">
    <Modal @close="toggleModal2">
      <p>this is a new modal</p>
    </Modal>
  </div>
  <button @click="toggleModal2">show modal 2</button>
</template>

<script>
import Modal from './components/Modal';
import Tester from './components/Tester';
import Slots from './components/Slots';

export default {
  name: 'App',
  components: {
    Modal,
    Tester,
    Slots,
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
      showModal2: false,
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
    toggleModal2() {
      this.showModal2 = !this.showModal2;
      console.log(this.showModal2);
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

<template>
  <h1>this is another vue component</h1>
  <p>I will use this component in App</p>
  <h2 :class="false ? footerClass : ''">{{ header }}</h2>
  <!-- you can run js simple stuff like this when you call the : -->
  <p :class="footerClass">{{ footer }}</p>
  <!-- because I'm trying to bind data I need to use the :, if I don't use the colon then it will just take exactly what is wrapped in the quotes -->
  <h3>{{ counter }}</h3>
  <button @click="decreaseCounter">Decrement</button>
  <button @click="increaseCounter">Increment</button>
  <button @click.shift="changeCounter">Do something crazy</button>
  <!-- click event modifiers -->
  <button @click="changeBackToZero">Change it back to a number</button>

  <div>
    <h1 @click="secretEvent">{{ one }}</h1>
    <h1 v-if="showSecret">{{ secretMessage }}</h1>
    <h2>{{ two }}</h2>
    <h3>{{ three }}</h3>
  </div>
</template>

<script>
export default {
  data() {
    return {
      footer: 'I can extract data from here too.',
      footerClass: 'foot',
      // this is data that the component can use.
      counter: 0,
      secretMessage: 'this is a secret message',
    };
  },
  props: ['header', 'one', 'two', 'three', 'showSecret'],
  // if I'm receiving a prop from an attribute that is in the parent component, I need to extract it here.
  methods: {
    increaseCounter() {
      this.counter++;
    },
    decreaseCounter() {
      this.counter--;
    },
    changeCounter() {
      this.counter = 'why would you press that btn?';
    },
    changeBackToZero() {
      this.counter = 0;
    },
    secretEvent() {
      this.$emit('press');
    },
  },
};
</script>

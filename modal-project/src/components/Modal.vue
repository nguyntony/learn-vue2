<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <h1>{{ header }}</h1>
      <p>{{ text }}</p>
      <p>{{ obj.content }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['header', 'text', 'obj', 'theme'],
  methods: {
    closeModal() {
      // we connected this with the backdrop div and when the user clicks the div, it'll emit this custom event, now you are able to use this custom event int he parent component. and like how we use @click for the event listener, here we can now use @close
      this.$emit('close');
    },
  },
};
</script>

<style scoped>
/* when adding the scoped attribute to the style tag, this will include some sort of UID to the classes in the css, there is a slight performance hit bc vue needs to inject all of these attributes */
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
.modal h1 {
  /* you could instead make the selector look more specific */
  color: coral;
}
.modal.sale {
  background: crimson;
  color: white;
}
.modal.sale h1 {
  color: white;
}
</style>

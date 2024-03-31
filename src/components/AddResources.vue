<template>
  <form>
    <input type="text" placeholder="Insert a title" v-model="title" />
    <input
      type="text"
      placeholder="Insert a description"
      v-model="description"
    />
    <input type="text" placeholder="Insert a link" v-model="link" />
    <button @click.prevent="sendItem">Send</button>
  </form>

  <teleport to="body">
    <ErrorModal v-if="showError" class="error">
      <p>An error ocurred!</p>
      <p>Input fields must not be empty</p>
      <button @click="hideError()">Ok</button>
    </ErrorModal>
  </teleport>
</template>

<script>
import ErrorModal from './ErrorModal.vue';

export default {
  data() {
    return {
      title: null,
      description: null,
      link: null,
      showError: false,
    };
  },
  props: ['addItem'],
  components: {
    ErrorModal,
  },
  emits: ['addItem'],
  methods: {
    sendItem() {
      if (
        this.title === null ||
        this.description === null ||
        this.link === null
      ) {
        this.showError = true;
      } else {
        this.$emit('addItem', {
          id: new Date().toLocaleString(),
          title: this.title,
          description: this.description,
          link: this.link,
        });

        this.title = null;
        this.description = null;
        this.link = null;
      }
    },
    hideError() {
      this.showError = false;
    },
  },
};
</script>

<style scoped>
form {
  position: relative;
  width: 50%;
  display: flex;
  flex-wrap: wrap;
  padding: 20px 10px;
  min-height: 100px;
  background-color: rgb(255, 167, 167);
  border-radius: 10px;

  input {
    width: 45%;
    height: 25px;
    border-radius: 6px;
    border: 1px solid lightgray;
    margin: 0 15px 10px 0;
    padding: 2px 8px;
  }

  button {
    position: absolute;
    right: 20px;
    bottom: 10px;
    border-radius: 6px;
    width: 60px;
    height: 30px;
    border: 1px solid lightgray;
    background-color: rgb(255, 0, 0);
    color: white;
    font-size: 14px;
    font-weight: 700;
  }

  button:hover {
    cursor: pointer;
  }
}
</style>

<template>
  <div
    @click="selectComponent('stored')"
    :class="selected === 'stored' ? 'selected' : ''"
  >
    Stored Resources
  </div>

  <div
    @click="selectComponent('add')"
    :class="selected === 'add' ? 'selected' : ''"
  >
    Add a resource
  </div>
</template>

<script>
export default {
  props: ['defineComponent'],
  methods: {
    selectComponent(name) {
      this.selected = name;
      this.$emit('defineComponent', name);
    },
  },
  emits: ['defineComponent'],
  data() {
    return {
      selected: false,
    };
  },
};
</script>

<style scoped>
div {
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
  border: 1px solid lightgray;
  min-height: 45px;
  width: 15%;
}

div:hover {
  cursor: pointer;
}

.selected {
  background-color: rgb(255, 229, 234);
}
</style>

<template>
  <button>
    <slot></slot>
  </button>
</template>

<style scoped>
button {
  width: 40px;
  height: 30px;
  position: absolute;
  bottom: 20px;
  right: 20px;
  background-color: rgb(255, 116, 116);
  color: white;
  font-weight: 700;
  border: none;
  border-radius: 8px;
}

button:hover {
  cursor: pointer;
}
</style>

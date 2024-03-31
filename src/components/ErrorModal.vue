<template>
  <div></div>
  <dialog open>
    <slot></slot>
  </dialog>
</template>

<style scoped>
div {
  position: absolute;
  z-index: 1;
  top: 0;
  height: 100%;
  width: 100%;
  background-color: rgba(146, 146, 146, 0.658);
}
dialog {
  position: absolute;
  z-index: 2;
  top: 10%;
  width: 40%;
  height: 10%;
  border-radius: 8px;
  border: 1px solid lightgray;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>

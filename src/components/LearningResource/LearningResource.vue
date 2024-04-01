<template>
  <div
    class="resource-item"
    v-for="resource in resources.slice().reverse()"
    :key="resource.id"
  >
    <div class="contents">
      <p>Title: {{ resource.title }}</p>
      <p>Description: {{ resource.description }}</p>
      <a :href="resource.link" target="_blank">View Resource</a>
      <button @click="() => removeItem(resource.id)">Delete</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['resources'],
  inject: ['removeItem'],
};
</script>

<style>
.resource-item {
  width: 50%;
  height: 150px;
  background-color: #f9f6ee;
  border: 1px solid lightgray;
  border-radius: 10px;
  margin-bottom: 15px;
}

.contents {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  width: 95%;
  height: 90%;
  margin: 5px auto;

  p {
    width: fit-content;
  }

  a {
    width: fit-content;
  }

  button {
    position: absolute;
    top: 5px;
    right: 5px;
    border: 1px solid lightgray;
    border-radius: 6px;
    width: 60px;
    height: 30px;
    background-color: rgb(255, 50, 50);
    color: white;
    font-size: 14px;
    font-weight: 700;
  }

  button:hover {
    cursor: pointer;
  }
}
</style>

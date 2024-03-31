<template>
  <section>
    <LearningResource
      v-if="resources.length !== 0"
      :resources="resources"
      class="learning-resource"
    />
    <p v-else>There are no resources yet!</p>
  </section>
</template>

<script>
import LearningResource from './LearningResource/LearningResource.vue';

export default {
  data() {
    return {};
  },
  props: ['removeItem', 'resources'],
  components: {
    LearningResource,
  },
};
</script>

<style scoped>
section {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

p {
  font-size: 16px;
  font-weight: 600;
}
</style>

<template>
  <TheHeader />
  <main>
    <section class="navigator">
      <ComponentSelector @defineComponent="defineComponent" />
    </section>

    <section class="container">
      <StoredResources
        v-if="selectedComponent === 'stored'"
        :resources="resources"
      />

      <KeepAlive>
        <AddResource v-if="selectedComponent === 'add'" @addItem="addItem" />
      </KeepAlive>
    </section>
  </main>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import StoredResources from './components/StoredResources.vue';
import AddResource from './components/AddResources.vue';
import ComponentSelector from './components/ComponentSelector.vue';

export default {
  data() {
    return {
      selectedComponent: null,
      resources: [],
    };
  },
  components: {
    TheHeader,
    StoredResources,
    AddResource,
    ComponentSelector,
  },
  methods: {
    defineComponent(name) {
      this.selectedComponent = name;
    },
    removeItem(id) {
      this.resources = this.resources.filter((item) => {
        return item.id !== id;
      });
    },
    addItem(item) {
      this.resources.push(item);
    },
  },
  provide() {
    return {
      removeItem: this.removeItem,
    };
  },
};
</script>

<style scoped>
main {
  margin: 10px;
}

.navigator {
  margin-top: 25px;
  display: flex;
  justify-content: space-evenly;
  font-size: 18px;
}

.container {
  margin-top: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>

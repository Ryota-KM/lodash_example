<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/lodash_logo.png" />
    <div class="menu">
      <span
        v-for="(name, k) in list"
        :key="k"
        @click="setComponent(name)"
        class="menu_item"
      >
        {{ name }}
      </span>
    </div>
    <div><component :is="currentComponent"></component></div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import debounce from './components/debounce.vue';
import pick from './components/pick.vue';
import orderby from './components/orderby.vue';

export default Vue.extend({
  name: 'App',
  components: {
    debounce,
    pick,
    orderby
  },

  data() {
    return {
      name: ''
    };
  },

  computed: {
    currentComponent(): string {
      return this.name ?? '';
    },

    list() {
      return ['debounce', 'pick', 'orderby'];
    }
  },

  methods: {
    setComponent(name: string) {
      this.name = name;
    }
  }
});
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
img {
  width: 100px;
}
.menu_item {
  cursor: pointer;
}
</style>

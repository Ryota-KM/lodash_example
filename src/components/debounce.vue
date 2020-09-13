<template>
  <div>
    <input type="text" ref="tagText" v-model="text" />
    <p>{{ text }}</p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import _ from 'lodash';

export default Vue.extend({
  data() {
    return {
      text: ''
    };
  },

  methods: {
    alm() {
      alert(this.text);
    }
  },

  watch: {
    text: {
      handler: _.debounce(function(this: Vue & { alm(): void }) {
        this.alm();
      }, 2000),
      deep: true
    }
  }
});
</script>

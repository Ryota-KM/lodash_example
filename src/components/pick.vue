<template>
  <div>
    {{ pick }}
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import _ from 'lodash';

export default Vue.extend({
  data() {
    return {
      original: {
        name: 'john',
        age: 30,
        country: 'USA'
      }
    };
  },

  computed: {
    pick(this: Vue & { original: {} }) {
      const original = this.original;
      return _.pick(original, ['name', 'country']);
    }
  }
});
</script>

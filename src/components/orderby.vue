<template>
  <div>
    <div>
      <div v-for="(user, i) in orderDesc" :key="i">
        <span>{{ user.name }}: {{ user.age }}</span>
      </div>
    </div>
    <div>
      <p @click="increment('tony')">tony ++</p>
      <p @click="increment('hulk')">hulk ++</p>
      <p @click="increment('thor')">thor ++</p>
      <p @click="increment('steve')">steve ++</p>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import _ from 'lodash';

// NOTE: npm i --save-dev lodash.orderby

export default Vue.extend({
  data() {
    return {
      users: [
        { name: 'tony', age: 48 },
        { name: 'hulk', age: 34 },
        { name: 'thor', age: 47 },
        { name: 'steve', age: 36 }
      ]
    };
  },

  computed: {
    orderDesc(this: Vue & { users: { user: string; age: number } }) {
      return _.orderBy(this.users, ['age', 'name'], ['desc', 'asc']);
    }
  },

  methods: {
    increment(name: string) {
      const target = this.users.find(u => u.name === name) as {
        name: string;
        age: number;
      };
      target.age++;
    }
  }
});
</script>

<style>
p {
  cursor: pointer;
}
</style>

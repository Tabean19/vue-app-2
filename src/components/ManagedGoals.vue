<template>
  <h2>Managed Goals</h2>
  <input type="text" v-model="inputValue" @keydown.enter="setGoals" />
  <button @click="setGoals">Set Goal</button>
  <teleport to="body">
    <ErrorAlert v-if="inputIsInvalid">
      <h2>Input is invalid!</h2>
      <p>Please enter a valid goal...</p>
      <button @click="closeErr">Okay</button>
    </ErrorAlert>
  </teleport>
  <ul>
    <li v-for="goal in goals" :key="goal.id">{{ goal }}</li>
  </ul>
</template>

<script>
import ErrorAlert from './ErrorAlert.vue';

export default {
  components: {
    ErrorAlert,
  },
  data() {
    return {
      goals: [],
      inputValue: '',
      inputIsInvalid: false,
    };
  },
  methods: {
    setGoals() {
      if (this.inputValue === '') {
        this.inputIsInvalid = true;
        // alert('Please enter a goal');
        // throw new Error('Please enter a goal');
      } else {
        this.goals = [this.inputValue, ...this.goals];
        this.inputValue = '';
      }
    },
    closeErr() {
      this.inputIsInvalid = false;
    },
  },
};
</script>

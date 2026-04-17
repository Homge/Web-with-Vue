<template>
  <form action="#" @submit.prevent="onSubmit">
    <p v-if="errorsPresent" class="error">Please fill out all fields!</p>
    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class="germany flag"></i> German
      </div>
      <input type="text" placeholder="Enter word..." v-model="word.german" />
    </div>

    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class="united kingdom flag"></i> English
      </div>
      <input type="text" placeholder="Enter word..." v-model="word.english" />
    </div>

    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class="spain flag"></i> Spanish
      </div>
      <input type="text" placeholder="Enter word..." v-model="word.spanish" />
    </div>
    <router-link :to="{name:'words'}">Show</router-link>
  </form>
</template>

<script>
export default {
  name: 'word-form',
  props: {
    word: {
      type: Object,
      required: false,
      default: () => ({ english: '', german: '', spanish: '' })
    }
  },
  data() {
    return {
      errorsPresent: false
    };
  },
  methods: {
    onSubmit() {
      console.log('Submitting:', this.word); 
      if (!this.word.english || !this.word.german || !this.word.spanish) {
        this.errorsPresent = true;
        this.$emit('error', 'Please fill out all fields!');
      } else {
        this.errorsPresent = false;
        this.$emit('create-or-update', this.word);
      }
    }
  }
};
</script>

<style scoped>
.error {
  color: red;
}
</style>
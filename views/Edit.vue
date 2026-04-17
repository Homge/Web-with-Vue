<template>
  <div>
    <h1>Edit Word</h1>
    <word-form @create-or-update="createOrUpdate" @error="handleError" :word="word"></word-form>
  </div>
</template>

<script>
import WordForm from '../components/Show.vue';
import { api } from '../helpers/helpers';

export default {
  name: 'edit',
  components: {
    'word-form': WordForm
  },
  data() {
    return {
      word: {}
    };
  },
  async mounted() {
    try {
      this.word = await api.getWord(this.$route.params.id);
    } catch (error) {
      this.flash('Failed to load word: ' + error.message, 'error');
    }
  },
  methods: {
    async createOrUpdate(word) {
      console.log('Updating:', word); 
      try {
        if (!word.english || !word.german || !word.spanish) {
          this.flash('Please fill out all fields!', 'error');
          return;
        }
        await api.updateWord(word);
        this.flash('Word updated successfully!', 'success');
        this.$router.push(`/words/${word._id}`);
      } catch (error) {
        this.flash('Failed to update word: ' + error.message, 'error');
      }
    },
    handleError(message) {
      this.flash(message, 'error');
    }
  }
};
</script>
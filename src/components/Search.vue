<template>
  <div style="max-width: 350px">
      <q-banner v-show="this.error" inline-actions class="text-white bg-red q-mt-xl">
        {{ this.error }}
      </q-banner>
      <q-form
      @submit.prevent="search"
      >
        <q-input
        debounce="1000"
        filled
        placeholder="Search"
        bg-color="blue-grey-12"
        class="q-mt-xl"
        v-model="this.word"
        @keypress="this.error=''"
        >
        <template v-slot:append>
          <q-icon name="search" />
        </template>
        </q-input>
      </q-form>

      <q-list class="q-mt-xl" dark bordered separator style="max-width: 318px">
      <q-item clickable v-ripple>
        <q-item-section>
          <q-item-label>Word</q-item-label>
          <q-item-label caption>{{this.word}}</q-item-label>
        </q-item-section>
      </q-item>

      <q-item clickable v-ripple>
        <q-item-section>
          <q-item-label>Meaning</q-item-label>
          <q-item-label caption>{{this.wordDefinition}}</q-item-label>
        </q-item-section>
      </q-item>

      <q-item clickable v-ripple>
        <q-item-section>
          <q-item-label>Usage</q-item-label>
          <q-item-label>{{this.wordUsage}}</q-item-label>
        </q-item-section>
      </q-item>
    </q-list>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
    return {
      word: '',
      wordData: '',
      wordDefinition: '',
      wordUsage: '',
      error:''
    }
  },
  methods: {
    search() {
      axios.get(`https://api.dictionaryapi.dev/api/v2/entries/en/${this.word}`)
      .then((res) => {
        this.wordData = res.data;
        this.wordDefinition = this.wordData[0].meanings[0].definitions[0].definition;
        this.wordUsage = this.wordData[0].meanings[0].definitions[0].example;
        console.log(this.wordData[0].meanings[0].definitions[0]);
        console.log(this.wordData[0].meanings[0].definitions[0].definition);
        console.log(this.wordData[0].word);
      })
      .catch((err) => {
        this.error = 'We were not able to find the word in our dictionary, we are deeply sorry.'
      })
    }
  }
}
</script>



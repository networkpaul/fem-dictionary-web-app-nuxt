<template>
  <div class="container mx-auto search-input">
    <form @submit.prevent="checkValidity">
      <input ref="input" class="search-label" :class="{ 'is-invalid': !isValid }" @blur="checkValidity" type="text"
             placeholder="Search for any word..." v-model="tempWord" @keyup.enter="fetchData">
      <button class="search-button" type="submit"></button>
    </form>
    <span v-if="!isValid" class="search-error">Whoops, can’t be empty…</span>
  </div>
  <WordInfo v-if="wordDefinition"
            :word="wordDefinition"
            :phonetic="phonetic"
            :noun="noun"
            :verb="verb"
            :noun-def1="nounDef1"
            :noun-def2="nounDef2"
            :noun-def3="nounDef3"
            :verb-def1="verbDef1"
            :verb-def1-example="verbDef1Example"
            :syn1="syn1"
            :syn2="syn2"
            :syn3="syn3"
            :source-link="sourceLink"
  />
</template>

<script>

import axios from "axios";

export default {
  name: 'SearchInput',
  data() {
    return {
      error: false,
      isValid: true,
      tempWord: '',
      word: '',
      wordDefinition: '',
      phonetic: '',
      noun: '',
      nounDef1: '',
      nounDef2: '',
      nounDef3: '',
      syn1: '',
      syn2: '',
      syn3: '',
      syn4: '',
      syn5: '',
      verb: '',
      verbDef1: '',
      verbDef1Example: '',
      sourceLink: ''
    }
  },
  methods: {
    checkValidity() {
      this.isValid = this.$refs.input.value
    },
    fetchData() {
      this.error = false
      this.wordDefinition = ''
      this.phonetic = ''
      this.noun = ''
      this.nounDef1 = ''
      this.nounDef2 = ''
      this.nounDef3 = ''
      this.syn1 = ''
      this.syn2 = ''
      this.syn3 = ''
      this.syn4 = ''
      this.syn5 = ''
      this.verb = ''
      this.verbDef1Example = ''
      this.verbDef1 = ''
      this.sourceLink = ''

      axios
          .get(`https://api.dictionaryapi.dev/api/v2/entries/en/${this.tempWord}`)
          .then(response => {
            this.word = response.data
            this.wordDefinition = this.word[0].word
            this.phonetic = this.word[0].phonetic
            this.noun = this.word[0].meanings[0].partOfSpeech
            this.nounDef1 = this.word[0].meanings[0].definitions[0].definition
            this.nounDef2 = this.word[0].meanings[0].definitions[1].definition
            this.nounDef3 = this.word[0].meanings[0].definitions[2].definition
            this.syn1 = this.word[0].meanings[0].synonyms[0]
            this.syn2 = this.word[0].meanings[0].synonyms[1]
            this.syn3 = this.word[0].meanings[0].synonyms[2]
            this.verb = this.word[1].meanings[0].partOfSpeech
            this.verbDef1 = this.word[1].meanings[0].definitions[0].definition
            this.verbDef1Example = this.word[1].meanings[0].definitions[0].example
            this.sourceLink = this.word[0].sourceUrls[0]

            console.log(this.word)
            console.log(this.verbDef1Example)
          })
          .catch(() => {
            this.error = true
            console.log('error!!')
            console.log(this.word)
          })
    }
  }
}
</script>
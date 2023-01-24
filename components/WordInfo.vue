<template>
  <div class="container wordInfo">
    <div class="wordInfo-word">
      <div class="word-word">
        <h1 class="word-prim" v-if="word">{{ word }}</h1>
        <p class="word-pronunciation" v-if="phonetic">{{ phonetic }}</p>
      </div>
      <div class="word-play">
        <svg xmlns="http://www.w3.org/2000/svg" width="75" height="75" viewBox="0 0 75 75">
          <g fill="#A445ED" fill-rule="evenodd">
            <circle cx="37.5" cy="37.5" r="37.5" opacity=".25"/><path d="M29 27v21l21-10.5z"/>
          </g>
        </svg>
      </div>
    </div>
    <div class="wordInfo-definition">
      <h3 class="word-section" v-if="noun">{{ noun }}</h3>
      <div class="word-meaning">
        <h4 v-if="nounDef1">Meaning</h4>
        <ul>
          <li v-if="nounDef1">{{ nounDef1 }}</li>
          <li v-if="nounDef2">{{ nounDef2 }}</li>
          <li v-if="nounDef3">{{ nounDef3 }}</li>
        </ul>
        <div class="word-synonyms">
          <h4 v-if="syn1">Synonyms</h4>
          <h5 v-if="syn1">{{ syn1 }}</h5>
          <h5 v-if="syn2">{{ syn2 }}</h5>
          <h5 v-if="syn3">{{ syn3 }}</h5>
        </div>
      </div>
    </div>
    <div class="wordInfo-definition">
      <h3 class="word-section" v-if="verb">{{ verb }}</h3>
      <div class="word-meaning">
        <h4 v-if="verbDef1">Meaning</h4>
        <ul>
          <li v-if="verbDef1">{{ verbDef1 }}</li>
        </ul>
        <p class="word-example" v-if="verbDef1Example">"{{ verbDef1Example }}"</p>
      </div>
    </div>
    <div class="wordInfo-source" v-if="sourceLink">
      <div class="wordInfo-sourceText">
        <h6 class="source">Source</h6>
        <a :href="sourceLink" class="source-link" target="_blank">{{ sourceLink }}
          <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 14 14"><path fill="none" stroke="#838383" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6.09 3.545H2.456A1.455 1.455 0 0 0 1 5v6.545A1.455 1.455 0 0 0 2.455 13H9a1.455 1.455 0 0 0 1.455-1.455V7.91m-5.091.727 7.272-7.272m0 0H9m3.636 0V5"/></svg>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: [ 'word', 'phonetic', 'noun', 'verb', 'nounDef1', 'nounDef2', 'nounDef3', 'verbDef1', 'verbDef2', 'verbDef3', 'syn1', 'syn2', 'syn3', 'sourceLink', 'verbDef1Example']
}
</script>
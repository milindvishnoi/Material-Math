<template>
  <div class="question-container">
    <span v-katex:display="question" />
  </div>
</template>

<script>
import Vue from 'vue'
import VueKatex from 'vue-katex'

Vue.use(VueKatex)

export default {
  name: 'classic-question',
  props: {
    question: String
  }
}
</script>

<style>
@import "../../node_modules/katex/dist/katex.min.css";

.katex {
  font-size: 3em;
  justify-self: center;
  margin-top: 100px;
}

.katex-html {
  color: white;
  margin-top: -42px;
}
</style>

<template>
  <div id="container">
    <div v-if="start == true">
      <Domanda @result="quizResult" />
    </div>
    <div v-else>
      <div v-if="result != null">
        <div :key="index" v-for="(question, index) in result">
          <p>
            {{ question.question }}
          </p>
          <h4>Risposta Corretta: {{ question.correct }}</h4>
          <h4 v-if="question.correctId != question.selectedId">
            Risposta Selezionata: {{ question.selected }}
          </h4>
        </div>

        <button @click="startGame()">
          <h3>Start New Game</h3>
        </button>
      </div>

      <button v-else @click="startGame()">
        <h3>Start Game</h3>
      </button>
    </div>
  </div>
</template>

<script>
import Domanda from "./Domanda.vue";

export default {
  name: "Container",
  components: {
    Domanda,
  },
  props: {
    msg: String,
  },

  data() {
    return {
      result: null,
      start: false,
    };
  },

  methods: {
    quizResult: function (params) {
      console.log(params);
      this.result = params;
      if (this.start) {
        this.start = false;
      }
    },

    startGame() {
      this.start = true;
      this.result = null;
    },
  },
};
</script>
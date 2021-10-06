<template>
  <div id="question">
    <Risposte @risposteToDomanda="answersFromRisposte" />
    <!-- Question -->
    <div>
      <div :key="index" v-for="(question, index) in questions">
        <h2 v-if="index == counter">
          {{ question.text }}
        </h2>
      </div>
    </div>
    <!-- /Question -->

    <!-- Answers -->
    <div :key="index" v-for="(answer, index) in answers">
      <div v-if="index == counter">
        <button
          v-on:click="selectAnswer(answer.correct, index, counter)"
          :key="index"
          v-for="(risp, index) in answer.risp"
          :class="selected == index ? right : selected != index ? wrong : ''"
          :disabled="enableDisable"
        >
          {{ risp.r }}
        </button>
      </div>
    </div>
    <!-- /Answers -->

    <!-- Next Question -->
    <button @click="selectQuestion()" :disabled="enableDisableNext">
      Next Question
    </button>
    <!-- /Next Question -->
  </div>
</template>

<script>
import Risposte from "./Risposte.vue";

export default {
  name: "Domanda",
  components: {
    Risposte,
  },

  props: {
    data: Object,
  },

  data() {
    return {
      questions: [
        { text: "domanda 1" },
        { text: "domanda 2" },
        { text: "domanda 3" },
        { text: "domanda 4" },
        { text: "domanda 5" },
        { text: "domanda 6" },
        { text: "domanda 7" },
        { text: "domanda 8" },
        { text: "domanda 9" },
      ],

      answers: [],
      counter: null,
      right: null,
      wrong: null,
      questionCounter: [],
      selected: null,
      quizResult: [],
      enableDisableNext: true,
    };
  },

  methods: {
    answersFromRisposte: function (params) {
      this.answers = params;
    },

    randomNumber(number) {
      return Math.floor(Math.random() * number);
    },

    sendResult() {
      this.$emit("result", this.quizResult).data;
    },

    selectQuestion() {
      let randNumber = this.randomNumber(this.questions.length);

      if (!this.questionCounter.includes(randNumber)) {
        this.counter = randNumber;
        this.questionCounter.push(randNumber);
      } else if (this.questionCounter.length != this.questions.length) {
        this.selectQuestion();
      } else {
        this.counter = null;
        this.questionCounter = [];
        this.sendResult();
      }
      this.selected = null;
      this.right = null;
      this.wrong = null;
      this.enableDisable = false;
      this.enableDisableNext = true;
    },

    /**
     * Select answer and return correctAnswer id, clicked button id and question id
     * params @int correctAnswer
     * params {int}
     * params {int}
     */
    selectAnswer(correctAnswer, buttonId, id) {
      // console.log(correctAnswer, buttonId, id);

      if (buttonId == correctAnswer) {
        this.right = "bg-green";
        this.enableDisableNext = false;
        this.enableDisable = true;
      } else {
        this.right = "bg-green";
        this.wrong = "bg-red";
        this.enableDisableNext = false;
        this.enableDisable = true;
      }
      this.selected = correctAnswer;

      // Send data to Container
      this.quizResult.push({
        correct: this.answers[id].risp[correctAnswer].r,
        selected: this.answers[id].risp[buttonId].r,
        question: this.questions[id].text,
        correctId: correctAnswer,
        selectedId: buttonId,
      });
    },
  },

  mounted() {
    this.selectQuestion();
    this.quizResult = [];
  },
};
</script>

<style lang="scss">
.bg-green {
  background-color: greenyellow;
}

.bg-red {
  background-color: red;
}
</style>
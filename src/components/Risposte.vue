<template>
  <div></div>
</template>

<script>
export default {
  name: "Risposte",
  props: {
    data: Object,
  },

  data() {
    return {
      answers: [
        {
          risp: [
            { r: "risp 1" },
            { r: "risp 2" },
            { r: "risp 3" },
            { r: "risp 4" },
          ],
          correct: 2,
        },
        {
          risp: [
            { r: "risp 5" },
            { r: "risp 6" },
            { r: "risp 7" },
            { r: "risp 8" },
          ],
          correct: 2,
        },
        {
          risp: [
            { r: "risp 9" },
            { r: "risp 10" },
            { r: "risp 11" },
            { r: "risp 12" },
          ],
          correct: 2,
        },
        {
          risp: [
            { r: "risp 13" },
            { r: "risp 14" },
            { r: "risp 15" },
            { r: "risp 16" },
          ],
          correct: 2,
        },
        {
          risp: [
            { r: "risp 17" },
            { r: "risp 18" },
            { r: "risp 19" },
            { r: "risp 20" },
          ],
          correct: 2,
        },
        {
          risp: [
            { r: "risp 21" },
            { r: "risp 22" },
            { r: "risp 23" },
            { r: "risp 24" },
          ],
          correct: 2,
        },
        {
          risp: [
            { r: "risp 25" },
            { r: "risp 26" },
            { r: "risp 27" },
            { r: "risp 28" },
          ],
          correct: 2,
        },
        {
          risp: [
            { r: "risp 29" },
            { r: "risp 30" },
            { r: "risp 31" },
            { r: "risp 32" },
          ],
          correct: 0,
        },
        {
          risp: [
            { r: "risp 33" },
            { r: "risp 34" },
            { r: "risp 35" },
            { r: "risp 36" },
          ],
          correct: 3,
        },
        // {
        //   risp: [
        //     { r: "risp 37" },
        //     { r: "risp 38" },
        //     { r: "risp 39" },
        //     { r: "risp 40" },
        //   ],
        //   correct: 3,
        // },
      ],
    };
  },

  methods: {},

  mounted() {
    this.$emit("risposteToDomanda", this.answers).data;
  },
};
</script>


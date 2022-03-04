<template>
  <h1>Vue クイズ</h1>
  <div id="app">
    <h2>Q.{{ quiz.text }}</h2>
    <h3>ヒント：東京上野の不忍池を洋画で描いた人物です。</h3>
    <img id="quizImage" v-bind:src="quizImagePath" v-bind:alt="quiz.text" />
    <div class="container">
      <button
        v-for="(choice, i) in quiz.choices"
        v-bind:key="i"
        v-on:click="choiced(choice)"
      >
        {{ choice.text }}
      </button>
    </div>
    <div>{{ feedback }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      feedback: "",
      quiz: {
        text: "日本で初めてコーヒーミルを作ったとされる人物はどれでしょう？",
        image: "Coffee MIll.jpg",
        choices: [
          {
            text: "平賀源内",
            isCorrect: false,
            feedback:
              "残念!平賀源内は、エレキテルを修理した事で知られる蘭学者だよ!。",
          },
          {
            text: "司馬江漢",
            isCorrect: false,
            feedback:
              "正解!司馬江漢は、江戸時代後期に活躍した洋画家兼蘭学者。東海道五十三次のオリジナルを描いたとされる謎の多い人物だよ!!",
          },
          {
            text: "大田南畝",
            isCorrect: true,
            feedback:
              "惜しい!大田南畝は、日本で初めてコーヒーの味や風味を記録したとされる人物だよ!!",
          },
        ],
      },
    }
  },
  methods: {
    choiced(choice) {
      this.feedback = choice.feedback

      if (choice.isCorrect) {
        // 次の問題へ
      }
    },
  },
  computed: {
    quizImagePath() {
      return "./images/" + this.quiz.image
    },
  },
}
</script>

<style>
#app {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
#quiz-image {
  height: 300px;
  width: 300px;
  object-fit: contain;
}
.container {
  display: flex;
  height: 2em;
  width: 300px;
  padding: 1em;
  justify-content: space-around;
}
</style>

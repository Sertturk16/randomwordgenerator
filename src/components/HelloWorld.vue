<template>
  <v-container>
    <v-row>
      <v-col>
        <template v-if="!submitted">
          <v-textarea
            :flat="true"
            label="Enter Words"
            class="words-textarea"
            v-model="words"
            color="primary"
            solo
            bg-color="primary"
          ></v-textarea>
          <v-btn class="primary" @click="saveWords" :disabled="!words.length"
            >Save Words</v-btn
          >
        </template>
        <template v-else>
          <div>
            <div class="word-card-wrapper text-center">
              <v-alert color="primary" prominent style="color: #fff">
                {{ currentWord.trim() }}
              </v-alert>
            </div>
            <div class="text-center mb-2">
              <span>{{ wordsArr.length }} words left.</span>
            </div>
            <div class="d-flex justify-center">
              <v-btn
                class="primary mr-2"
                :disabled="!this.wordsArr.length"
                @click="generateNewWord()"
                >Next</v-btn
              >
              <v-btn @click="restart()" class="primary">Restart</v-btn>
            </div>
          </div>
        </template>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "HelloWorld",
  data: () => ({
    words: "",
    nextDisable: false,
    currentWord: null,
    submitted: false,
    wordsArr: [],
    poppedWordsArr: [],
  }),
  methods: {
    saveWords() {
      this.wordsArr = this.words.split(",");
      this.submitted = true;
      this.generateNewWord();
    },
    generateNewWord() {
      let i = Math.floor(Math.random() * this.wordsArr.length);
      this.currentWord = this.wordsArr.splice(i, 1)[0];
      this.poppedWordsArr.push(this.currentWord);
    },
    restart() {
      this.nextDisable = false;
      this.currentWord = null;
      this.submitted = false;
      this.wordsArr = [];
      this.poppedWordsArr = [];
    },
  },
};
</script>

<style>
.words-textarea .v-input__slot {
  background: #e3f2fd !important;
}
</style>
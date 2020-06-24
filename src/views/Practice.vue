<template>
  <div class="practice">
    <div class="vertical-stack">
      <v-btn class="mx-2" fab dark small color="primary" @click="updateNumberOfPoints">
        <h1 class="number-of-points">{{this.numPoints + 1}}</h1>
      </v-btn>

      <v-btn class="mx-2" fab dark small color="primary" @click="$emit('roulette', numPoints)">
        <v-icon dark>loop</v-icon>
      </v-btn>
    </div>
    <div class="vertical-stack">
      <textarea class="practiceTxtArea" id="field" placeholder="何かここに書きましょう！(Write something here!)"></textarea>
    </div>
    <div class="vertical-stack">
      <v-btn class="mx-2" fab dark small color="primary" @click="toggleWanaKana">
        <syllabary-hiragana-icon />
      </v-btn>

      <v-btn class="mx-2" fab dark small color="primary" @click="send">
        <v-icon dark>send</v-icon>
      </v-btn>
    </div>
  </div>
</template>

<script>
  import * as wanakana from 'wanakana'
  import SyllabaryHiraganaIcon from 'vue-material-design-icons/SyllabaryHiragana.vue'

  export default  {
    name: "Practice",
    imeEnabled: false,
    props: ["selectedPoints"],

    components: {
      SyllabaryHiraganaIcon
    },

    data() {
      return {
        numPoints: 0
      }
    },

    methods: {
      toggleWanaKana() {
        let practiceTxtArea = document.getElementsByClassName("practiceTxtArea");
        if(this.imeEnabled) {
          wanakana.unbind(practiceTxtArea[0])
        } else {
          wanakana.bind(practiceTxtArea[0]);
        }
        this.imeEnabled = !this.imeEnabled;
      },

      updateNumberOfPoints() {
        this.numPoints = (this.numPoints + 1) % 3;
        this.$emit('roulette', this.numPoints);
      },


      send() {
        document.getElementById("field").value = "";
      }

    }
  }
</script>

<style scoped>
  .vertical-stack {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 5px;
  }

  .practice {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }

  .practiceTxtArea {
    resize: none;
    overflow: auto;
    width: 70vw;
    height: 7vh;
    color: #c7d1e0;
    border: dotted black 1px;
  }

  .vertical-stack {
    height: 50%;
  }
</style>
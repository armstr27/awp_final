<template>
  <div class="home">

    <div class="top">
      <v-app-bar fixed class="bar">
        <v-expansion-panels
                v-model="panel"
                :disabled="disabled"
                multiple
        >
          <v-expansion-panel id="practice-panel" class="panel" v-on:change="onExpand"
                             style="background:#b32e8a;color:White">
            <v-expansion-panel-header class="header">
              <h1 id="roulette">
                Pick at least 3 grammar points to start!
              </h1>
            </v-expansion-panel-header>
            <v-expansion-panel-content class="content">
              <Practice v-on:roulette="roulette"/>
            </v-expansion-panel-content>
            <v-expansion-panel-header expand-icon="">
              <v-icon>expand_less</v-icon>
            </v-expansion-panel-header>
          </v-expansion-panel>
        </v-expansion-panels>
      </v-app-bar>
    </div>

    <div class="chapters">
      <div v-for="chapter in $options.grammarData.chapters" v-bind:key="chapter.number">
        <Chapter v-bind:chapter="chapter" v-on:select-point="updatePointList"/>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

import Chapter from "../components/Chapter";
import GRAMMAR_DATA from '../data/grammar.json'
import Practice from "./Practice";

export default {

  name: 'Grammar',
  components: {
    Practice,
    Chapter
  },

  grammarData: GRAMMAR_DATA,

  data() {
    return {
      disabled: true,
      readonly: false,
      selectedPoints: [],
      expanded: false
    }
  },

  methods: {
    updatePointList(name) {
      var index = this.selectedPoints.indexOf(name);
      let roulette = document.getElementById("roulette");
        if(index > -1) {
          this.selectedPoints.splice(index, 1);
        } else {
          this.selectedPoints.push(name);
        }

        if(this.selectedPoints.length < 3) {
          roulette.textContent = "Pick at least 3 grammar points to start!";
          this.disabled = true;
        } else if (!this.expanded) {
          roulette.textContent = "Click here when ready to practice!";
          this.disabled = false;
        }
    },

    onExpand() {
      this.expanded = !this.expanded;
      let roulette = document.getElementById("roulette");
      if(this.expanded) {
        roulette.textContent = "Press the Loop button to begin practicing!";
      } else {
        if(this.selectedPoints.length < 3) {
          roulette.textContent = "Pick at least 3 grammar points to start!";
        } else {
          roulette.textContent = "Click here when ready to practice!";
        }
      }
      console.log(this.expanded);
    },

    roulette(numPoints) {
      let roulette = document.getElementById("roulette");
      var availablePoints = this.selectedPoints.slice();
      var rouletteText = "Write a sentence using: ";

      for(var i = 0; i <= numPoints; i++) {
        if(i != 0 && i == numPoints) {
          rouletteText += ", and ";
        } else if (i != 0 && i < numPoints) {
          rouletteText += ", ";
        }
        var selection = Math.floor(Math.random() * availablePoints.length);
        rouletteText += availablePoints[selection];
        availablePoints.splice(selection, 1);
      }
      roulette.textContent = rouletteText;
    }
  }

}
</script>

<style>

  .header {
    margin-top: 20vh;
  }

  .chapters {
    margin-top: 25vh;
    margin-left: 15vw;
    margin-right: 15vw;

    display: grid;
    grid-template-columns: 30vw 30vw 30vw;
    grid-gap: 10px;
    justify-content: space-around;
    align-items: center;
  }
</style>

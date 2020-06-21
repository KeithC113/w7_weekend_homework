<template>
  <div id="app">
    <h1> World Cup 2018 Stato</h1>
    <matches-by-round-filter :matches="matches"> </matches-by-round-filter>
    <match-detail :match="selectedMatch"> </match-detail>
  </div>
</template>

<script>
import MatchesByRoundFilter from './components/MatchesByRoundFilter.vue'
import MatchDetail from './components/MatchDetail.vue'
import {eventBus} from './main.js'

export default {
  name: 'app',
  data(){
    return {
      matches:[],
      stage: "",
      selectedMatch: null
    }
  },
  mounted(){
    this.getMatches(),

    eventBus.$on('match-selected', (match)=> {this.match = selectedMatch})
  },
  methods:{
    getMatches: function(){
      fetch('https://world-cup-json-2018.herokuapp.com/matches')
      .then(response => response.json())
      .then(matches => this.matches = matches)
      .then(() => this.filterRounds("First stage")
    )},
    filterRounds: function(stage){
      return this.matches.filter((match)=> {
        return match.stage_name !== stage;
      })
    }
  },
  components: {
    'matches-by-round-filter': MatchesByRoundFilter,
    'match-detail': MatchDetail
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

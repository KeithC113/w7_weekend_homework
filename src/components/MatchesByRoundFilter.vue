<template lang="html">
    <form v-on:submit.prevent>
      <select v-on:change="handleSelect" v-model="selectedMatch">
        <option disabled value=""> Choose a match...</option>
        <option v-for="(match, index) in matches" :value="match" v-bind:key="index">{{match.stage_name}} : {{match.home_team_country}} V {{match.away_team_country}}</option>
      </select>
    </form>
</template>
<script>
import {eventBus} from "../main.js"

export default {
  name: 'matches-by-round-filter',
  data(){
    return{
      "selectedMatch": null
    }
  },
  props:['matches'],
  methods:{
    handleSelect(){
      eventBus.$emit('match-selected', this.selectedMatch)
    }
  }
}
</script>

<style lang="css" scoped>
</style>

<template lang="html">
  <div v-if="match">
    <div id="match-detail-container">
      <div id="match-detail">
        <h1>{{match.home_team_country}} V {{match.away_team_country}}</h1>
        <ul v-on:click="handleClick">
          <p id="score">Score> More info... </p>
          <p id="venue">Venue > More info... </p>
          <p id="attendance" >Attendance > More info... </p>
          <p> Home Team Starting 11 > More info... </p>
          <p>Away Team Starting 11 > More info... </p> -->
        </ul>
        <!-- <ul>
        <li>Game > {{match.home_team_country}} V {{match.away_team_country}}</li>
        <li>Score> {{match.home_team.goals}} V {{match.away_team.goals}} </li>
        <li>Venue > {{match.venue}}</li>
        <li>Attendance > {{match.attendance}}</li>
        <li> Home Team Starting 11 </li> <li>Away Team Starting 11</li>
      </ul> -->
    </div>
  </div>
</div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'match-detail',
  props: ['match'],
  methods:{
    handleClick: function (){
      eventBus.$emit("detail-info", this.match);
    }
  }
}
</script>

<style lang="css" scoped>

#match-detail-container{
  width:70%;
}

#match-detail {
  text-align: left;
  display: flex;
}

#match-text {
  margin-left: 10%;
  margin-right: 10%;
  /* word-wrap: normal; */
}

li.{
  list-style-type: none;
  margin: 10;
  padding: 10;
}
</style>

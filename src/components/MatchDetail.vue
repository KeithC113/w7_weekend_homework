<template lang="html">
    <div id="match-detail-container">
      <div id="match-detail">
        <h1> {{match}} </h1>
        <!-- <h1> {{match.home_team_country}} V {{match.away_team_country}} </h1> -->
        <!-- <div id="match-text">
          <p>{{match.venue}}</p>
        </div> -->
      </div>
    </div>

</template>

<script>

// import {eventBus} from '../main.js'
export default {
  name: 'match-detail',
  props: ['match']
}
</script>

<style lang="css" scoped>

#match-detail-container{
  width:55%
}

#match-detail {
  display: flex;
}

#match-text {
  margin-left: 10%;
  margin-right: 10%;
  word-wrap: normal;

}
</style>

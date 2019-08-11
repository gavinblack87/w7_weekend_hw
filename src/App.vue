<template>
  <div>
    <team-select :teams="teams" />
    <team-info :team="selectedTeam" />
  </div>
</template>

<script>
import { eventBus } from '@/main.js';
import TeamSelect from '@/components/TeamSelect.vue';
import TeamInfo from '@/components/TeamInfo.vue';

export default {
  components: {
    'team-select': TeamSelect,
    'team-info': TeamInfo
  },
  data() {
    return {
      teams: [],
      selectedTeam: null
    };
  },
  mounted() {
    eventBus.$on('team-selected', (selectedIndex) => {
      this.selectedTeam = this.teams.data[selectedIndex];
    });
    fetch("https://www.balldontlie.io/api/v1/teams")
    .then(res => res.json())
    .then(teams => this.teams = teams)
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<template lang="html">
  <select @change="teamSelected">
    <option selected disabled> - </option>
    <option v-for="(team, index) in teams.data" :value="index">{{ team.full_name }}</option>
  </select>
</template>

<script>
import { eventBus } from '@/main.js';

export default {
  name: 'team-select',
  props: ['teams'],
  methods: {
    teamSelected(e) {
      const selectedIndex = e.target.value;
      eventBus.$emit('team-selected', selectedIndex);
    }
  }
}
</script>

<style lang="css" scoped>
</style>

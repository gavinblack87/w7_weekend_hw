<template lang="html">
  <ul v-if="team !== null">
    <li>{{ team.full_name }}</li>
    <li><span class="bold">Home City:</span>{{ team.city }}</li>
    <li><span class="bold">Abbreviation:</span>{{ team.abbreviation }}</li>
    <li><span class="bold">Divinsion:</span>{{ team.division }}</li>
  </ul>
</template>

<script>
export default {
  name: 'team-info',
  props: ['team']
}
</script>

<style lang="css" scoped>
.bold {
  font-weight: bold;
}
</style>

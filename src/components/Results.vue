<template>
  <div>
    <p>Reaction time: {{ score }} ms</p>
  </div>
</template>

<script>
export default {
  name: 'ResultsComponent',
  props: ['score']
}
</script>
<template>
  <div id="app">
    <Robot />
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {
    Robot: () => import('./components/Robot')
  }
}
</script>

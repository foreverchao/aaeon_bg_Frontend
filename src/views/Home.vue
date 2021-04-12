<template>
  <div class="home">
    <global-header></global-header>
  </div>
</template>

<script>
// @ is an alias to /src

import GlobalHeader from '../components/GlobalHeader.vue'

export default {
  name: 'Home',
  components: {
    GlobalHeader
  }
}
</script>

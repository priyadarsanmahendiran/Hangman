<template>
  <div class="home">
    <entry-vue></entry-vue>
  </div>
</template>

<script>
import EntryVue from '../components/Entry.vue'

export default {
  name: 'Home',
  components: {
    EntryVue
  }
}
</script>

<style scoped>
    .home{
      padding-top: 200px;
    }
</style>

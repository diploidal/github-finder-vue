<template>
  <Header instruction="Search for a Github username to start..."/>
  <Profile/>
</template>

<script>
import Header from './components/Header.vue'
import Profile from './components/Profile.vue'

export default {
  name: 'App',
  components: {
    Header,
    Profile
  }
}
</script>

<style>
</style>

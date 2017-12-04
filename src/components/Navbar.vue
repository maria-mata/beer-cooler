<template>
  <nav class="navbar is-primary">
    <div class="navbar-brand">
      <h1 class="title is-white">Beer Cooler</h1>
    </div>
    <div class="navbar-menu">
      <div class="navbar-end">
        <add/>
      </div>
    </div>
  </nav>
</template>

<script>
import Add from './Add'

export default {
  name: 'Navbar',
  components: {
    Add
  }
}
</script>

<style lang="css">
</style>

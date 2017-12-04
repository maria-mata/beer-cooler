<template>
  <div>
    <nav class="navbar is-dark">
      <div class="container">
        <div class="navbar-brand">
          <p class="navbar-item heading is-size-4">Beer Cooler</p>
        </div>
        <div class="navbar-menu">
          <div class="navbar-end">
            <!-- Add a Beer Form -->
            <add :beers="beers" :addBeer="addBeer"/>
          </div>
        </div>
      </div>
    </nav>
    <section class="section">
      <div class="container">
        <!-- List of Beers Here  -->
        <div class="columns is-multiline">
          <beer v-for="beer in beers" :beer="beer" key="beer.id"
          :addLike="addLike" :removeLike="removeLike"/>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
const proxy = 'https://cors-anywhere.herokuapp.com/'
const api = 'http://beer.fluentcloud.com/v1/beer'
const url = proxy + api

import Beer from './Beer'
import Add from './Add'

export default {
  name: 'Home',
  components: {
    Beer,
    Add
  },
  data() {
    return {
      beers: []
    }
  },
  async mounted() {
    const data = await fetch(url)
    const response = await data.json()
    this.beers = response
  },
  methods: {
    addLike(id, likes) {
      const settings = {
        method: 'PUT',
        headers: {
          'content-type': 'application/json'
        },
        body: JSON.stringify({
          likes: JSON.stringify(likes + 1)
        })
      }
      fetch(`${url}/${id}`, settings)
    },
    removeLike(id) {
      console.log(id);
    },
    addBeer(beer) {
      console.log(beer);
    }
  }
}
</script>

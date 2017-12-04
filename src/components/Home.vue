<template>
  <section class="section">
    <div class="container">
      <div class="content">
        <!-- Add a Beer Form -->
        <add :addBeer="addBeer"/>
      </div>
      <!-- List of Beers Here  -->
      <div class="columns is-multiline">
        <beer v-for="beer in beers" :beer="beer" key="beer.id"
        :updateLikes="updateLikes"/>
      </div>
    </div>
  </section>
</template>

<script>
const proxy = 'https://cors-anywhere.herokuapp.com/'
const api = 'http://beer.fluentcloud.com/v1/beer'
const url = proxy + api

import Add from './Add'
import Beer from './Beer'

export default {
  name: 'Home',
  components: {
    Add,
    Beer
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
    addBeer(beer) {
      const settings = {
        method: 'POST',
        headers: {
          'content-type': 'application/json'
        },
        body: JSON.stringify({
          name: beer,
          likes: '0'
        })
      }
      fetch(url, settings)
      .then(response => {
        response.json()
        location.reload()
      })
    },
    updateLikes(id, likes) {
      const settings = {
        method: 'PUT',
        headers: {
          'content-type': 'application/json'
        },
        body: JSON.stringify({
          likes: JSON.stringify(likes)
        })
      }
      fetch(`${url}/${id}`, settings)
    }
  }
}
</script>

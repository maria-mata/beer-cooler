<template>
  <form @submit.prevent="handleAddBeer(beer)">
    <div class="field has-addons">
      <p class="control">
        <input class="input is-medium" type="text" placeholder="Add a new beer" v-model="beer">
      </p>
      <p class="control">
        <button class="button is-medium is-info">
          Add
        </button>
      </p>
    </div>
  </form>
</template>

<script>
export default {
  name: 'Add',
  props: ['addBeer'],
  data() {
    return {
      beer: ''
    }
  },
  methods: {
    handleAddBeer(beer) {
      this.addBeer(beer)
      this.beer = ''
    }
  }
}
</script>

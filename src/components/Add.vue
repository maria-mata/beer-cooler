<template>
  <div class="level">
    <div class="level-left">
      <form class="level-item" @submit.prevent="handleAddBeer">
        <div class="field has-addons">
          <p class="control">
            <input class="input" type="text" placeholder="Add a new beer" v-model="beer">
          </p>
          <p class="control">
            <button class="button is-info">
              Add
            </button>
          </p>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Add',
  props: ['beers', 'addBeer'],
  data() {
    return {
      beer: ''
    }
  },
  methods: {
    handleAddBeer() {
      this.addBeer(this.beer)
      this.beer = ''
    }
  }
}
</script>

<template>
  <div class="column is-one-third-desktop">
    <div class="box">
      <article class="media">
        <div class="media-content">
          <div class="content">
            <p>
              {{ beer.name }} ({{ this.likesCount }} likes)
            </p>
          </div>
          <nav class="level is-mobile">
            <div class="level-left">
              <a class="level-item" @click.prevent="likeBeer(beer.id, beer.likes)">
                <span class="icon"><i class="fa fa-thumbs-up"></i></span>
              </a>
              <a class="level-item" @click.prevent="unlikeBeer(beer.id, beer.likes)">
                <span class="icon"><i class="fa fa-thumbs-down"></i></span>
              </a>
            </div>
          </nav>
        </div>
      </article>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Beer',
  props: ['beer', 'updateLikes', 'removeLike'],
  computed: {
    likesCount() {
      return this.beer.likes
    }
  },
  methods: {
    likeBeer(id, likes) {
      this.beer.likes = likes + 1
      this.updateLikes(id, this.beer.likes)
    },
    unlikeBeer(id, likes) {
      likes - 1 < 0 ? this.beer.likes = 0 : this.beer.likes = likes - 1
      this.updateLikes(id, this.beer.likes)
    }
  }
}
</script>

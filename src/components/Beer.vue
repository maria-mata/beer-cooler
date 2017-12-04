<template>
  <div class="column is-one-third-desktop">
    <div class="box">
      <article class="media">
        <div class="media-content">
          <div class="content">
            <p>
              {{ beer.name }} ({{ beer.likes }} likes)
            </p>
          </div>
          <nav class="level is-mobile">
            <div class="level-left">
              <a class="level-item" @click.prevent="addLike(beer.id, beer.likes)">
                <span class="icon"><i class="fa fa-thumbs-up"></i></span>
              </a>
              <a class="level-item" @click.prevent="removeLike(beer.id, beer.likes)">
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
  props: ['beer', 'addLike', 'removeLike']
}
</script>

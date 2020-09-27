<template>
  <div class="box">
    <article class="media">
      <div class="media-left">
        <figure class="image is-64x64">
          <img
            :src="
              image ? image : `https://bulma.io/images/placeholders/128x128.png`
            "
            alt="Image"
          />
        </figure>
      </div>
      <div class="media-content">
        <div class="content">
          <p>
            <strong>{{ title }}</strong> <small>@{{ slug }}</small>
            <small>31m</small>
            <br />
            {{ text }}
          </p>
        </div>
        <nav class="level is-mobile">
          <div class="level-left">
            <a class="level-item" aria-label="reply">
              <span class="icon is-small">
                <i class="bx bx-reply"></i>
              </span>
            </a>
            <a class="level-item" aria-label="retweet">
              <span class="icon is-small">
                <i class="bx bx-repost"></i>
              </span>
            </a>
            <a class="level-item" aria-label="like">
              <span class="icon is-small">
                <i class="bx bxs-heart"></i>
              </span>
            </a>
          </div>
        </nav>
      </div>
    </article>
  </div>
</template>

<script>
export default {
  props: ['image', 'title', 'text', 'slug'],
  created() {
    console.log('box created', this.props)
  },
}
</script>

<style></style>

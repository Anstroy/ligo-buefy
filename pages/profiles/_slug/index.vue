<template>
  <div class="">
    <div class="columns is-vcentered">
      <div class="column is-one-quarter flex justify-center">
        <figure class="image is-128x128">
          <img
            class="is-rounded"
            src="https://bulma.io/images/placeholders/128x128.png"
          />
        </figure>
      </div>
      <div class="column">
        <h1 class="title">
          {{ profile.name }}
        </h1>
        <h2 class="subtitle">
          {{ profile.title }}
        </h2>

        <div class="buttons">
          <a class="button is-info">
            <strong><i class="bx bx-plus"></i> Seguir</strong>
          </a>
          <a class="button is-light"
            ><i class="bx bxs-conversation"></i> Mensaje
          </a>
        </div>
      </div>
    </div>

    <section>
      <b-tabs position="is-centered">
        <b-tab-item label="Inicio">
          <div class="columns">
            <div class="column is-one-third">
              <div class="box">
                <article class="media">
                  <div class="media-content">
                    <div class="content">
                      <p>
                        <i class="bx bxs-info-circle"></i>
                        <strong>Information</strong>
                      </p>
                      <p>
                        {{ profile.description }}
                      </p>
                      <p>
                        <i class="bx bx-user-pin"></i>
                        <strong>175 Seguidores</strong>
                      </p>
                      <p>
                        <i class="bx bx-user-pin"></i>
                        Retos <span class="tag">{{ retos.length }}</span>
                      </p>
                      <p>
                        <i class="bx bx-envelope"></i>
                        {{ profile.email }}
                      </p>
                    </div>
                    <nav class="level is-mobile">
                      <div class="level-left">
                        <a class="level-item" aria-label="reply">
                          <span class="icon is-small">
                            <i class="fas fa-reply" aria-hidden="true"></i>
                          </span>
                        </a>
                        <a class="level-item" aria-label="retweet">
                          <span class="icon is-small">
                            <i class="fas fa-retweet" aria-hidden="true"></i>
                          </span>
                        </a>
                        <a class="level-item" aria-label="like">
                          <span class="icon is-small">
                            <i class="fas fa-heart" aria-hidden="true"></i>
                          </span>
                        </a>
                      </div>
                    </nav>
                  </div>
                </article>
              </div>
            </div>
            <div class="column">
              <BoxComponent
                v-for="post in posts"
                :key="post.id"
                :title="profile.name"
                :slug="profile.slug"
                :text="post.text"
              />
            </div>
          </div>
        </b-tab-item>

        <b-tab-item :label="`Retos ${retos.length}`">
          <RetosComponent :retos="retos" />
        </b-tab-item>

        <b-tab-item label="Info">
          What light is light, if Silvia be not seen? <br />
          What joy is joy, if Silvia be not by— <br />
          Unless it be to think that she is by <br />
          And feed upon the shadow of perfection? <br />
          Except I be by Silvia in the night, <br />
          There is no music in the nightingale.
        </b-tab-item>
      </b-tabs>
    </section>
  </div>
</template>

<script>
import RetosComponent from '@/components/Retos'
import BoxComponent from '@/components/Bulma/box'

import retos from '@/data/retos'
import posts from '@/data/posts'

export default {
  components: {
    RetosComponent,
    BoxComponent,
  },
  props: ['profile'],
  data: () => ({
    retos: retos.reverse(),
    posts,
  }),
  created() {
    this.retos = retos.filter((r) => r.publisher === this.profile.id)
    this.posts = posts.filter((p) => p.profile === this.profile.id)
  },
}
</script>

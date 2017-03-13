<template>
  <div class="top">
    <md-layout :md-gutter="4">
      <md-layout v-for="article in articles" md-flex-xsmall="100" md-flex-small="50" md-flex-medium="33">
        <md-card>
          <md-card-media>
            <img src="assets/card-image-1.jpg" alt="People">
          </md-card-media>

          <md-card-header>
            <div class="md-title">
              {{ article.title }}
            </div>
            <div class="md-subhead">Subtitle here</div>
          </md-card-header>

          <md-card-actions>
            <md-button>Action</md-button>
            <md-button>Action</md-button>
          </md-card-actions>

          <md-card-content>
            content
          </md-card-content>
        </md-card>
      </md-layout>
    </md-layout>
  </div>
</template>

<script>
  export default {
    name: 'top',
    data() {
      return {
        articles: [
          { title: 'foo' },
          { title: 'bar' },
          { title: 'hoge' },
          { title: 'fuga' },
        ],
      };
    },
  };
</script>

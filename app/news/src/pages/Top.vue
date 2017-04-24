<template>
  <div class="top">
    <md-layout md-gutter="40">
      <md-layout md-flex="30" class="article-card" v-for="article in articles">
        <md-card md-with-hover style="width: 100%">
          <md-card-media v-if="article.thumbnail">
            <img :src="article.thumbnail" alt="thumbnail" />
          </md-card-media>

          <md-card-header>
            <div class="md-title">
              {{ article.title }}
            </div>
            <!--<div class="md-subhead">Subtitle here</div>-->
          </md-card-header>

          <md-card-content>
            {{ article.body }}
          </md-card-content>

          <md-card-actions>
            <md-button class="md-icon-button">
              <md-icon>favorite</md-icon>
            </md-button>
            <md-button class="md-icon-button" :href="article.url" target="_blank">
              <md-icon>link</md-icon>
            </md-button>
          </md-card-actions>
        </md-card>
      </md-layout>
    </md-layout>
    <md-button @click.native="more" v-if="isNext">more</md-button>
  </div>
</template>

<script>
  export default {
    name: 'top',
    data() {
      return {
        articles: [],
        limit: 3,
        offset: 0,
        isNext: false,
      };
    },
    created() {
      console.log('Top page is created');
      this.fetchArticles();
    },
    methods: {
      fetchArticles() {
        console.log('fetch articles');
        fetch(`http://localhost:8080/v1?limit=${this.limit}&offset=${this.offset}`)
          .then(response => response.json())
          .then((json) => {
            console.log(json);
            const articles = json.articles;
            if (articles.length > 0) {
              this.articles = this.articles.concat(articles);
            }
            this.offset = json.nextOffset;
            this.isNext = json.isNext;
          });
      },
      more() {
        console.log('more');
        this.fetchArticles();
      },
    },
  };
</script>

<style>
  .article-card {
    margin-bottom: 16px;
  }
</style>

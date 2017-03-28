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

          <!--<md-card-actions>-->
            <!--<md-button>Action</md-button>-->
            <!--<md-button>Action</md-button>-->
          <!--</md-card-actions>-->

          <md-card-content>
            {{ article.body }}
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
        articles: [],
      };
    },
    created() {
      console.log('Top page is created');
      fetch('http://localhost:8080/')
        .then(response => response.json())
        .then((json) => {
          console.log(json);
          this.articles = json.articles;
        });
    },
  };
</script>

<style>
  .article-card {
    margin-bottom: 16px;
  }
</style>

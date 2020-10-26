<template>
  <div>
    <v-text-field v-model="query" label="Search"></v-text-field>
    <v-btn @click="searchManga" color="dark">Search</v-btn>
    <v-divider class="mt-5 mb-1"></v-divider>
    <div class="d-flex flex-wrap">
      <v-card
        v-for="manga in results"
        :key="manga.mal_id"
        class="ma-2"
        width="344px"
        height="230px"
        outlined
      >
        <v-list-item three-line>
          <v-list-item-content>
            <div class="overline mb-4">score:{{ manga.score }}</div>
            <v-list-item-title class="headline mb-1">
              {{ manga.title }}
            </v-list-item-title>
            <v-list-item-subtitle>{{ manga.synopsis }}</v-list-item-subtitle>
          </v-list-item-content>

          <img
            :src="manga.image_url"
            alt=""
            :style="{ width: '80px', height: '150px', marginTop: '20px' }"
          />
        </v-list-item>

        <v-card-actions>
          <v-btn outlined rounded text @click="mangaurl(manga)">Visit</v-btn>
        </v-card-actions>
      </v-card>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      query: '',
      results: [],
    }
  },
  methods: {
    searchManga() {
      const url =
        'https://api.jikan.moe/v3/search/manga?q=' + this.query + '&page=1'
      axios.get(url).then((res) => {
        console.log(res)
        this.results = res.data.results
      })
    },
    mangaurl(manga) {
      window.location = manga.url
    },
  },
}
</script>

<style></style>

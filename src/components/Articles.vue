<template>
  <div class="container container-md-6">
    <div class="card mx-auto my-4 shadow" v-for="article in articles" :key="article.idberita">
      <img class="card-img-top" :src="'https://sumedangkab.go.id/assets/uploads/' + article.gambar" />
      <div class="card-body">
        <h5 class="card-title">{{ article.judul }}</h5>
        <p class="card-text" v-html="article.isi"></p>
        <div class="card-footer d-flex mb-2">
          <p class="mr-auto">Penulis : {{ article.penulis }}</p>
          <p>Diterbitkan: {{ article.tanggal }}</p>
        </div>
        <button>Detail</button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      articles: [],
    };
  },
  created() {
    axios
      .get("https://sumedangkab.go.id/index.php/berita/apisumedangkab")
      .then((res) => {
        this.articles = this.articles.concat(res.data);
      })
      .catch((err) => console.log(err));
  },
};
</script>

<style>
</style>
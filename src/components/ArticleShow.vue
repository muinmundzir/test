<template>
  <div class="container container-md-6">
    <div class="card mx-auto my-4 shadow">
      <img class="card-img-top" :src="'https://sumedangkab.go.id/assets/uploads/' + article.gambar" />
      <div class="card-body">
        <h5 class="card-title"></h5>
        <p class="card-text" v-html="article.isi"></p>
        <div class="card-footer d-flex mb-2">
          <p class="mr-auto">Penulis :</p>
          <p>Diterbitkan:</p>
        </div>
        <a href="#" class="btn btn-primary">Kembali</a>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  created() {
    axios
      .get("https://sumedangkab.go.id/index.php/berita/apisumedangkab")
      .then((res) => {
        console.log(res.data);
        this.articles = this.articles.concat(res.data);
        console.log(this.articles);
      })
      .catch((err) => console.log(err));
  },
};
</script>

<style>
</style>
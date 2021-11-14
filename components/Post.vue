<template>
  <div>
    <div class="container mx-auto flex flex-wrap md:px-8 px-0">
      <!-- Post Section -->
      <section class="w-full md:w-2/3 flex flex-col items-center px-3">
        <article class="flex flex-col shadow my-4">
          <!-- Article Image -->
          <div class="post-image" :style="`background-image:url(${gambar})`" />
          <div class="bg-white flex flex-col justify-start p-6">
            <p class="text-blue-700 text-sm font-bold uppercase pb-4">
              {{ kategori }}
            </p>
            <h3 class="text-3xl font-bold pb-4">
              {{ judul }}
            </h3>
            <p class="text-sm">
              Published on {{ published }}
            </p>
            <hr class="my-4">
            <div class="pb-3">
              {{ isi }}
            </div>
          </div>
        </article>
      </section>

      <!-- Sidebar Section -->
      <aside class="w-full md:w-1/3 flex flex-col items-center px-3">
        <div class="w-full bg-white shadow flex flex-col my-4 p-6">
          <h5>judul</h5>
        </div>
      </aside>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Informasi',
  data () {
    return {
      berita: null,
      judul: null,
      kategori: null,
      published: null,
      isi: null,
      gambar: null
    }
  },
  mounted () {
    const url =
      'https://api.muhammadiyah-bna.org/informasi/' + this.$route.params.id
    axios
      .get(url, {
        headers: {
          Authorization: `Bearer ${process.env.SECRET_KEY}`
        }
      })
      .then((res) => {
        this.berita = res.data.data
        this.judul = this.berita.judul
        this.kategori = this.berita.kategori.kategori
        this.isi = this.berita.isi
        this.published = this.berita.created_at
        this.gambar = this.berita.gambar.original
      })
      .catch((err) => {
        alert(err)
      })
  }
}
</script>

<style>
.post-image {
  height: 400px;
  width: 100%;
  background-color: lightgray;
  background-size: cover;
  background-position: center center;
  background-repeat: no-repeat;
}
</style>

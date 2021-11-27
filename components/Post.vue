<template>
  <div>
    <div class="container mx-auto flex flex-wrap md:px-8 px-0">
      <!-- Post Section -->
      <section class="w-full md:w-2/3 flex flex-col items-center px-3">
        <article class="flex flex-col shadow my-4">
          <!-- Article Image -->
          <div
            class="post-image min-w-full"
            :style="`background-image:url(${gambar})`"
          />
          <div class="bg-white flex flex-col justify-start p-6">
            <p class="text-blue-700 text-sm font-bold uppercase pb-4">
              {{ kategori }}
            </p>
            <h3 class="text-3xl font-bold pb-4">
              {{ judul }}
            </h3>
            <p class="text-sm text-gray-500">
              Published {{ published }}
            </p>
            <hr class="my-4">
            <div class="pb-3" v-html="isi" />
          </div>
        </article>
      </section>

      <!-- Sidebar Section -->
      <aside class="w-full md:w-1/3 flex flex-col items-center px-3">
        <div class="w-full bg-white shadow flex flex-col my-4 p-6">
          <h5>Informasi Terbaru</h5>
          <hr class="my-3">
          <nuxt-link v-for="(related, i) of latest" :key="i" :to="related.slug">
            <div class="related-items flex mb-3 shadow-sm">
              <div
                class="w-1/3 font-bold related-image rounded-md"
                :style="`background-image: url(${related.gambar.medium})`"
              />
              <div class="w-2/3 px-2">
                <h4 class="line-clamp-2">
                  {{ related.judul }}
                </h4>
                <small
                  class="text-gray-500"
                >Published {{ related.created_at }}</small>
              </div>
            </div>
          </nuxt-link>
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
      gambar: null,
      latest: null
    }
  },
  mounted () {
    const url = process.env.API_URL + 'informasi/' + this.$route.params.id
    axios
      .get(url, {
        headers: {
          Authorization: `Bearer ${process.env.SECRET_KEY}`
        }
      })
      .then((res) => {
        this.berita = res.data.data
        this.latest = res.data.data.latest
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
  background-size: cover;
  background-position: center center;
  background-repeat: no-repeat;
}

.related-image {
  background-position: center center;
  background-size: cover;
  background-repeat: no-repeat;
}
</style>

<template>
  <section class="text-gray-600 body-font">
    <div class="md:px-8 px-2 md:py-16 py-20 mx-auto container">
      <h3 class="text-3xl text-center mb-3">
        Latest News
      </h3>
      <hr class="border border-2 bg-black w-40 m-auto">
      <div class="flex flex-wrap mt-4 justify-center">
        <div
          v-for="berita of beritas"
          :key="berita.id"
          class="sm:p-0 md:w-1/3 mb-2"
        >
          <div
            class="
              m-2
              h-full
              border-2 border-gray-200 border-opacity-60
              rounded-lg
              overflow-hidden
            "
          >
            <nuxt-link :to="'informasi/' + berita.slug">
              <img
                class="lg:h-48 md:h-36 w-full object-cover object-center"
                :src="berita.gambar.medium"
                alt="blog"
              >
            </nuxt-link>
            <div class="p-6">
              <h2
                class="
                  tracking-widest
                  text-xs
                  title-font
                  font-medium
                  text-gray-400
                  mb-1
                  uppercase
                "
              >
                {{ berita.kategori.kategori }}
              </h2>
              <h1 class="title-font text-lg font-medium text-gray-900 mb-3">
                {{ berita.judul }}
              </h1>
              <p class="leading-relaxed mb-3">
                {{ berita.deskripsi }}
              </p>
              <div class="flex justify-between items-center">
                <nuxt-link
                  :to="'informasi/' + berita.slug"
                  class="
                    text-green-700
                    inline-flex
                    items-center
                    md:mb-2
                    lg:mb-0
                  "
                >
                  Selengkapnya
                  <svg
                    class="w-4 h-4 ml-2"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                    stroke-width="2"
                    fill="none"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  >
                    <path d="M5 12h14" />
                    <path d="M12 5l7 7-7 7" />
                  </svg>
                </nuxt-link>
                <span
                  class="
                    text-gray-400
                    inline-flex
                    items-center
                    leading-none
                    text-sm
                  "
                >
                  <svg
                    class="w-4 h-4 mr-1"
                    stroke="currentColor"
                    stroke-width="2"
                    fill="none"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    viewBox="0 0 24 24"
                  >
                    <path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z" />
                    <circle cx="12" cy="12" r="3" /></svg>{{ berita.views }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Berita',
  props: {
    limit: Boolean
  },
  data () {
    return {
      beritas: []
    }
  },
  async mounted () {
    const url = 'https://api.muhammadiyah-bna.org/informasi'
    if (this.limit === true) {
      url.concat('?page=1&limit=3')
    }
    await axios
      .get(url, {
        headers: {
          Authorization: `Bearer ${process.env.SECRET_KEY}`
        }
      })
      .then((res) => {
        this.beritas = res.data.data
      })
      .catch((err) => {
        alert(err)
      })
  }
}
</script>

<template>
  <div class="p-4 md:w-1/3">
    <div
      class="
        h-full
        border-2 border-gray-200 border-opacity-60
        rounded-lg
        overflow-hidden
      "
    >
      <nuxt-link :to="'/donasi/' + donasi.id">
        <img
          class="lg:h-48 md:h-36 w-full object-cover object-center"
          :src="donasi.gambar"
          alt="blog"
        >
      </nuxt-link>
      <div class="p-6">
        <div class="relative pt-1">
          <div class="flex mb-2 items-center justify-between">
            <div>
              <span
                class="
                  text-xs
                  font-semibold
                  inline-block
                  py-1
                  px-2
                  uppercase
                  rounded-md
                  text-white
                "
                :class="range == 100 ? 'bg-green-400' : 'bg-yellow-400'"
              >
                {{ range == 100 ? 'Terkumpul' : 'Sedang Berlangsung' }}
              </span>
            </div>
            <div class="text-right">
              <span
                class="text-xs font-semibold inline-block"
                :class="range == 100 ? 'text-green-700' : 'text-yellow-700'"
              >
                {{ range }}%
              </span>
            </div>
          </div>
          <div
            class="overflow-hidden h-2 mb-4 text-xs flex rounded"
            :class="range == 100 ? 'bg-green-200' : 'bg-yellow-200'"
          >
            <div
              :style="'width:' + range + '%'"
              class="
                shadow-none
                flex flex-col
                text-center
                whitespace-nowrap
                text-white
                justify-center
              "
              :class="range == 100 ? 'bg-green-700' : 'bg-yellow-700'"
            />
          </div>
        </div>
        <h2
          class="
            tracking-widest
            text-xs
            title-font
              uppercase
            font-medium
            text-gray-400
            mb-1
          "
        >
          {{ donasi.kategori.kategori }}
        </h2>
        <h1 class="title-font text-lg font-medium text-gray-900 mb-2">
          {{ donasi.judul }}
        </h1>
        <small><strong>{{ formatCurrency(donasi.jumlah) }}</strong>
          terkumpul dari
          <strong>{{ formatCurrency(donasi.target) }}</strong></small>
        <hr class="my-3">
        <div class="flex justify-between items-center">
          <nuxt-link
            :to="'/donasi/' + donasi.id"
            class="text-green-700 inline-flex items-center md:mb-2 lg:mb-0"
          >
            Donasi
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
            class="text-gray-400 inline-flex items-center leading-none text-sm"
          >
            <svg
              class="mr-2"
              xmlns="http://www.w3.org/2000/svg"
              width="15"
              height="15"
              viewBox="0 0 24 24"
            >
              <path
                fill="#9ca3af"
                d="M17 3v-2c0-.552.447-1 1-1s1 .448 1 1v2c0 .552-.447 1-1 1s-1-.448-1-1zm-12 1c.553 0 1-.448 1-1v-2c0-.552-.447-1-1-1-.553 0-1 .448-1 1v2c0 .552.447 1 1 1zm13 13v-3h-1v4h3v-1h-2zm-5 .5c0 2.481 2.019 4.5 4.5 4.5s4.5-2.019 4.5-4.5-2.019-4.5-4.5-4.5-4.5 2.019-4.5 4.5zm11 0c0 3.59-2.91 6.5-6.5 6.5s-6.5-2.91-6.5-6.5 2.91-6.5 6.5-6.5 6.5 2.91 6.5 6.5zm-14.237 3.5h-7.763v-13h19v1.763c.727.33 1.399.757 2 1.268v-9.031h-3v1c0 1.316-1.278 2.339-2.658 1.894-.831-.268-1.342-1.111-1.342-1.984v-.91h-9v1c0 1.316-1.278 2.339-2.658 1.894-.831-.268-1.342-1.111-1.342-1.984v-.91h-3v21h11.031c-.511-.601-.938-1.273-1.268-2z"
              /></svg>{{ donasi.created_at }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: { donasi: Array },
  data () {
    return {
      range: 0
    }
  },
  mounted () {
    this.range = (this.donasi.jumlah / this.donasi.target) * 100
  },
  methods: {
    formatCurrency (val) {
      return new Intl.NumberFormat('id-ID', {
        style: 'currency',
        currency: 'IDR'
      }).format(val)
    }
  }
}
</script>

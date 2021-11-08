<template>
  <section class="text-gray-700 body-font overflow-hidden">
    <div class="container px-5 py-16 mx-auto">
      <div class="lg:w-4/5 mx-auto flex flex-wrap">
        <img
          alt="ecommerce"
          class="
            lg:w-1/2
            w-full
            lg:h-auto
            h-64
            object-cover object-center
            rounded
          "
          :src="donasi.gambar"
        >
        <div class="lg:w-1/2 w-full lg:pl-10 lg:py-6 mt-6 lg:mt-0">
          <h2
            class="text-md title-font uppercase text-gray-500 tracking-widest"
          >
            {{ kategori }}
          </h2>
          <h1 class="text-gray-900 text-3xl title-font font-medium mb-1">
            {{ donasi.judul }}
          </h1>
          <hr class="my-2">
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
                  Task in progress
                </span>
              </div>
              <div class="text-right">
                <span
                  class="text-xs font-semibold inline-bloc"
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
                :style="`width: ${range}%`"
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
          <h3 class="text-md">
            <strong>{{ formatCurrency(donasi.jumlah) }}</strong> terkumpul dari
            <strong>{{ formatCurrency(donasi.target) }}</strong>
          </h3>

          <div class="relative my-4">
            <label
              for="full-name"
              class="leading-7 text-sm text-gray-600"
            >Nama Lengkap</label>
            <input
              id="full-name"
              type="text"
              name="full-name"
              class="
                w-full
                bg-white
                rounded
                border border-gray-300
                focus:border-green-700 focus:ring-2 focus:ring-green-200
                text-base
                outline-none
                text-gray-700
                py-1
                px-3
                leading-8
                transition-colors
                duration-200
                ease-in-out
              "
              placeholder="Masukan Nama Lengkap"
              autocomplete="no"
            >
          </div>
          <div class="relative mb-4">
            <label
              for="email"
              class="leading-7 text-sm text-gray-600"
            >Email</label>
            <input
              id="email"
              type="email"
              name="email"
              class="
                w-full
                bg-white
                rounded
                border border-gray-300
                focus:border-green-700 focus:ring-2 focus:ring-green-200
                text-base
                outline-none
                text-gray-700
                py-1
                px-3
                leading-8
                transition-colors
                duration-200
                ease-in-out
              "
              placeholder="Masukan Email"
              autocomplete="no"
            >
          </div>

          <div class="relative mb-4">
            <label
              for="jumlah_donasi"
              class="leading-7 text-sm text-gray-600"
            >Jumlah Donasi</label>
            <input
              id="jumlah_donasi"
              v-model="jumlahDonasi"
              type="number"
              name="jumlah_donasi"
              class="
                w-full
                bg-white
                rounded
                border border-gray-300
                focus:border-green-700 focus:ring-2 focus:ring-green-200
                text-base
                outline-none
                text-gray-700
                py-1
                px-3
                leading-8
                transition-colors
                duration-200
                ease-in-out
              "
              placeholder="Masukan Jumlah Donasi"
              autocomplete="no"
            >
          </div>
          <p class="leading-relaxed mb-4">
            Donasi kamu akan berkontribusi
            <strong> {{ (jumlahDonasi / donasi.target) * 100 }}%</strong> dari
            total kebutuhan.
          </p>
          <hr class="mb-4">
          <div class="flex">
            <span
              class="title-font font-medium text-2sm md:text-2xl text-gray-900"
            >{{ formatCurrency(jumlahDonasi) }}</span>
            <button
              class="
                flex
                ml-auto
                text-white
                bg-green-700
                border-0
                py-2
                px-6
                focus:outline-none
                hover:bg-green-500
                rounded
              "
            >
              Donasi
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      donasi: [],
      range: 0,
      kategori: null,
      jumlahDonasi: 0
    }
  },
  async mounted () {
    // alert(this.$route.params.id)
    const url =
      'https://api.muhammadiyah-bna.org/donasi/' + this.$route.params.id
    await axios
      .get(url, {
        headers: {
          Authorization: `Bearer ${process.env.SECRET_KEY}`
        }
      })
      .then((res) => {
        this.donasi = res.data.data
      })
      .catch((err) => {
        alert(err)
      })
    this.range = (this.donasi.jumlah / this.donasi.target) * 100
    this.kategori = this.donasi.kategori.kategori
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

<style></style>

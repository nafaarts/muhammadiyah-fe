<template>
  <section class="text-gray-700 body-font">
    <div class="lg:mx-8 sm:mx-2">
      <div class="container px-5 py-14 mx-auto">
        <h1 class="text-center text-4xl mb-4">
          Donasi
        </h1>
        <hr class="border border-2 m-auto bg-black w-40">
        <div class="flex flex-wrap">
          <donasi-card
            v-for="donasi of donasis.data"
            :key="donasi.id"
            :donasi="donasi"
            class="p-4 md:w-1/3"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import axios from 'axios'
import DonasiCard from './DonasiCard.vue'
export default {
  components: { DonasiCard },
  data () {
    return {
      donasis: []
    }
  },
  async mounted () {
    const url = 'https://api.muhammadiyah-bna.org/donasi'
    await axios
      .get(url, {
        headers: {
          Authorization: `Bearer ${process.env.SECRET_KEY}`
        }
      })
      .then((res) => {
        this.donasis = res.data
      })
      .catch((err) => {
        alert(err)
      })
  }
}
</script>

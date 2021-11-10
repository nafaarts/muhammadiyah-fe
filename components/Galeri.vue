<template>
  <section class="text-gray-600 body-font" data-aos="fade-down">
    <div class="md:px-8 px-2 py-16 mx-auto container">
      <img
        v-for="(img, i) of images.data"
        :key="i"
        class="img-galeri shadow-md md:border-4 border-1 border-white"
        :src="img.gambar.medium"
        :alt="img.deskripsi"
      >
    </div>
  </section>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      images: []
    }
  },
  async mounted () {
    const url = 'https://api.muhammadiyah-bna.org/gallery'
    await axios
      .get(url, {
        headers: {
          Authorization: `Bearer ${process.env.SECRET_KEY}`
        }
      })
      .then((res) => {
        this.images = res.data
      })
      .catch((err) => {
        alert(err)
      })
  }
}
</script>

<style scoped>
.container {
  column-count: 4;
  min-height: 100vh;
}

.img-galeri {
  width: 100%;
  height: auto;
  display: block;
  margin-bottom: 20px;
  padding: 10px;
  background: #fff;
  box-sizing: border-box;
}

@media screen and (max-width: 1024px) {
  .container {
    column-count: 3;
  }
}
@media screen and (max-width: 640px) {
  .container {
    column-count: 2;
  }
}
/* @media screen and (max-width: 375px) {
  .container {
    column-count: 2;
  }
} */
</style>

<template>
  <section class="text-gray-600 body-font" data-aos="fade-down">
    <div class="md:px-8 px-2 py-16 mx-auto container">
      <img
        v-for="(img, i) of images"
        :key="i"
        class="img-galeri shadow-md border-4 border-white"
        :src="'https://ancient-cliffs-36736.herokuapp.com' + img.gambar.formats.small.url"
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
    const token =
      'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiaWF0IjoxNjM1NDEzNjQ2LCJleHAiOjE2MzgwMDU2NDZ9.imEfxa_LndM3dJPXD6-0DdpTOcAC-DS7M3f6zlHFoBU'
    const url = 'https://ancient-cliffs-36736.herokuapp.com/galeris?_sort=created_at:DESC'
    await axios
      .get(url, {
        headers: {
          Authorization: `Bearer ${token}`
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
@media screen and (max-width: 375px) {
  .container {
    column-count: 1;
  }
}
</style>

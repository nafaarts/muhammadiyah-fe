<template>
  <section class="text-gray-600 body-font">
    <div class="md:px-8 px-2 mx-auto">
      <h3 class="text-3xl text-center mb-3">
        Galeri
      </h3>
      <hr class="border-2 bg-black w-40 m-auto mb-8">
      <div class="container">
        <transition-group tag="div" @before-enter="beforeEnter" @enter="enter">
          <img
            v-for="(img, i) of images.data"
            :key="i"
            :data-index="i"
            class="img-galeri shadow-md md:border-3 border-1 border-white"
            :src="img.gambar.medium"
            :alt="img.deskripsi"
            @click="showImage"
          >
        </transition-group>
      </div>
    </div>
  </section>
</template>

<script>
import axios from 'axios'
// eslint-disable-next-line import/no-named-as-default
import gsap from 'gsap'
export default {
  data () {
    const beforeEnter = (el) => {
      el.style.opacity = 0
      el.style.transform = 'translateY(100px)'
    }

    const enter = (el, done) => {
      gsap.to(el, {
        opacity: 1,
        y: 0,
        duration: 0.5,
        onComplete: done,
        delay: el.dataset.index * 0.2
      })
    }
    return {
      images: [],
      enter,
      beforeEnter
    }
  },
  async mounted () {
    const url = process.env.API_URL + 'gallery'
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
  },
  methods: {
    showImage (el) {
      console.log('src')
      // console.log(el.currentTarget.getAttribute('src'))
    }
  }
}
</script>

<style scoped>
.container {
  column-count: 4;
}

.img-galeri {
  width: 100%;
  height: auto;
  display: block;
  margin-bottom: 20px;
  padding: 10px;
  background: #fff;
  box-sizing: border-box;
  break-inside: avoid-column;
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

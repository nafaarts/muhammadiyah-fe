<template>
  <section class="text-gray-600 body-font bg-gray-50 md:px-8 px-2">
    <div class="container px-5 mx-auto py-24">
      <div class="flex flex-col text-center w-full mb-12">
        <h1 class="sm:text-3xl text-2xl font-medium title-font mb-4 text-gray-900">Pengurus PDM</h1>
        <p class="lg:w-2/3 mx-auto leading-relaxed text-base">
          kepengurusan Pimpinan Daerah Muhammadiyah
          periode
          <br />2021 - 2025
        </p>
      </div>
      <div class="flex flex-wrap">
        <div class="p-2 lg:w-1/3 md:w-1/2 w-full mx-auto" v-for="staff of staffs" v-bind:key="staff.id">
          <div class="h-full flex items-center border-gray-200 border p-4 rounded-lg">
            <img
              alt="team"
              class="w-16 h-16 bg-gray-100 object-cover object-center flex-shrink-0 rounded-full mr-4"
              :src="'https://ancient-cliffs-36736.herokuapp.com' + staff.gambar.url"
            />
            <div class="flex-grow">
              <h2 class="text-gray-900 title-font font-medium">{{staff.nama}}</h2>
              <p class="text-gray-500">{{staff.jabatan}}</p>
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
  data: () => {
    return {
      staffs: []
    }
  },
  async mounted () {
    const token =
      'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiaWF0IjoxNjM1NDEzNjQ2LCJleHAiOjE2MzgwMDU2NDZ9.imEfxa_LndM3dJPXD6-0DdpTOcAC-DS7M3f6zlHFoBU'
    const url = 'https://ancient-cliffs-36736.herokuapp.com/penguruses'
    await axios
      .get(url, {
        headers: {
          Authorization: `Bearer ${token}`
        }
      })
      .then((res) => {
        this.staffs = res.data
      })
      .catch((err) => {
        alert(err)
      })
  }
}
</script>

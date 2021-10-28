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
        <div class="p-2 lg:w-1/3 md:w-1/2 w-full mx-auto" v-for="sam of sample" v-bind:key="sam">
          <div class="h-full flex items-center border-gray-200 border p-4 rounded-lg">
            <img
              alt="team"
              class="w-16 h-16 bg-gray-100 object-cover object-center flex-shrink-0 rounded-full mr-4"
              src="https://dummyimage.com/80x80"
            />
            <div class="flex-grow">
              <h2 class="text-gray-900 title-font font-medium">Holden Caulfield</h2>
              <p class="text-gray-500">UI Designer</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data: () => {
    return {
      sample: [1, 2, 3, 4, 5, 6, 7]
    }
  }
}
</script>

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
          src="~assets/cta-panti.jpg"
        >
        <div class="lg:w-1/2 w-full lg:pl-10 lg:py-6 mt-6 lg:mt-0">
          <h2 class="text-sm title-font text-gray-500 tracking-widest">
            FOOD
          </h2>
          <h1 class="text-gray-900 text-3xl title-font font-medium mb-1">
            Bantu anak yatim untuk memenuhi kebutuhan gizinya
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
                    bg-yellow-400
                  "
                >
                  Task in progress
                </span>
              </div>
              <div class="text-right">
                <span
                  class="text-xs font-semibold inline-block text-yellow-700"
                >
                  30%
                </span>
              </div>
            </div>
            <div
              class="
                overflow-hidden
                h-2
                mb-4
                text-xs
                flex
                rounded
                bg-yellow-200
              "
            >
              <div
                style="width: 30%"
                class="
                  shadow-none
                  flex flex-col
                  text-center
                  whitespace-nowrap
                  text-white
                  justify-center
                  bg-yellow-700
                "
              />
            </div>
          </div>
          <h3 class="text-md">
            <strong>Rp 2.982.500</strong> terkumpul dari
            <strong>Rp 25.000.000</strong>
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
            Donasi kamu akan berkontribusi <strong>25%</strong> dari total
            kebutuhan.
          </p>
          <hr class="mb-4">
          <div class="flex">
            <span
              class="title-font font-medium text-2xl text-gray-900"
            >Rp 27.800</span>
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
            <button
              class="
                rounded-full
                w-10
                h-10
                bg-gray-200
                p-0
                border-0
                inline-flex
                items-center
                justify-center
                text-gray-500
                ml-4
              "
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="24"
                height="24"
                viewBox="0 0 24 24"
              >
                <path
                  fill="#383838"
                  d="M12 2c5.514 0 10 4.486 10 10s-4.486 10-10 10-10-4.486-10-10 4.486-10 10-10zm0-2c-6.627 0-12 5.373-12 12s5.373 12 12 12 12-5.373 12-12-5.373-12-12-12zm-6 17c1.513-6.587 7-7.778 7-7.778v-2.222l5 4.425-5 4.464v-2.223c0 .001-3.78-.114-7 3.334z"
                />
              </svg>
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {}
</script>

<style></style>

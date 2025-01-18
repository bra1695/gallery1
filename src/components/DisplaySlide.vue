<template>
  <main
    class="relative mb-24 min-h-[62.5rem] overflow-x-clip md:min-h-[68.75rem] lg:min-h-[40.625rem]"
    style="opacity: 1"
  >
    <article
      class="container absolute inset-x-0 mx-auto grid h-full grid-rows-[auto,1fr] px-6 md:space-y-20 lg:h-auto lg:min-h-[39rem] lg:grid-cols-[40.625rem_auto] lg:grid-rows-none lg:gap-x-[1.875rem] lg:space-y-0 xl:grid-cols-[53.4375rem_auto] xl:px-0"
      style="opacity: 1; transform: none"
    >
      <div class="relative h-[24.875rem] md:h-auto">
        <div class="relative max-w-[29.6875rem]">
          <img
            class="h-[17.5rem] w-full object-cover transition duration-200 ease-linear md:h-[35rem] md:w-[29.6875rem]"
            :src="item.images.hero.large"
            :alt="`Painting: ${item.name}`"
          />
          <button
          @click="openPopup"
            class="absolute left-4 top-4 flex min-h-10 items-center gap-4 bg-black/75 px-4 text-link2 uppercase text-white transition duration-300 hover:bg-white/25 focus:outline-none focus:ring-black focus-visible:ring-2 focus-visible:ring-offset-4 md:bottom-4 md:top-auto"
          >
            <img
              src="data:image/svg+xml,%3csvg%20width='12'%20height='12'%20xmlns='http://www.w3.org/2000/svg'%3e%3cg%20fill='%23FFF'%20fill-rule='nonzero'%3e%3cpath%20d='M7.714%200l1.5%201.5-2.357%202.357%201.286%201.286L10.5%202.786l1.5%201.5V0zM3.857%206.857L1.5%209.214%200%207.714V12h4.286l-1.5-1.5%202.357-2.357zM8.143%206.857L6.857%208.143%209.214%2010.5l-1.5%201.5H12V7.714l-1.5%201.5zM4.286%200H0v4.286l1.5-1.5%202.357%202.357%201.286-1.286L2.786%201.5z'/%3e%3c/g%3e%3c/svg%3e"
              alt="Expand icon"
            /><span class="pt-[2px]">View Image</span>
          </button>
        </div>
        <div
          class="absolute -bottom-1 -left-1 md:-top-1 md:bottom-auto md:left-auto md:right-0 lg:flex lg:h-full lg:flex-col lg:justify-between"
        >
          <div
            class="w-[17.5rem] space-y-2 bg-white p-6 md:w-[27.8125rem] md:px-[4.0625rem] md:pb-[4.0625rem] md:pt-0 lg:pr-6"
          >
            <h2
              class="text-heading2 md:text-heading1 lg:text-heading2 xl:text-heading1"
            >
              {{ item.name }}
            </h2>
            <h3 class="text-subhead1 text-gray-500">{{ item.artist.name }}</h3>
          </div>
          <div
            class="px-4 md:flex md:justify-end md:pr-[5.4375rem] lg:pr-0 xl:items-end xl:justify-start xl:pl-32"
          >
            <img
              class="size-16 object-cover md:size-32"
              :src="item.artist.image"
              :alt="`Picture of ${item.artist.name}`"
            />
          </div>
        </div>
      </div>
      <div class="relative max-w-[35.75rem]">
        <h2
          class="absolute right-0 top-0 -translate-y-5 text-display2 text-gray-100 md:left-0 md:right-auto md:-translate-y-2 md:text-display1 lg:left-auto lg:right-0 lg:text-display2 xl:text-display1"
        >
          {{ item.year }}
        </h2>
        <div
          class="relative z-10 flex h-full max-w-[28.5625rem] flex-col items-start justify-between gap-4 pb-14 pt-[6.5625rem] md:ml-auto lg:ml-0 lg:max-w-[21.875rem]"
        >
          <p class="text-gray-500">
            {{ item.description }}
          </p>
          <a
            class="text-link2 uppercase text-gray-500 underline transition duration-300 hover:text-black focus:outline-none focus:ring-black focus-visible:ring-2 focus-visible:ring-offset-4"
            :href="item.source"
            target="_blank"
            >Go to source</a
          >
        </div>
      </div>
    </article>
    <PopupView v-if="showPopup" @close="closePopup" :image="item.images.hero.large" :name="item.name" />

  </main>
</template>
<script>
import PopupView from './PopupView.vue';
export default {
  components:{
    PopupView
  },  
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      showPopup: false,
    };
  },
  methods: {
    openPopup() {
      this.showPopup = true; 
    },
    closePopup() {
      this.showPopup = false;
    },
  },
};
</script>

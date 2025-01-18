<template>
  <div class="container p-3.5 sm:px-4 md:px-8 lg:px-16 xl:px-16 mx-auto my-2">
    <DisplaySlide :item="selectedItem" />
  </div>
  <div
    class="max-w-8xl container fixed inset-x-0 bottom-0 z-20 mx-auto w-full bg-white"
  >
    <div class="h-[1px] bg-gray-300">
      <div
        class="h-[1px] bg-black transition-all duration-300"
        :style="{width: progressBarStep}"
      ></div>
    </div>
    <div
      class="flex min-h-[4.5rem] items-center justify-between px-6 py-4 md:min-h-24 md:px-10 md:py-6"
    >
      <div class="flex flex-col gap-2" style="opacity: 1">
        <h4 class="text-[0.875rem] leading-4 md:text-heading3">Starry Night</h4>
        <h5 class="text-[0.625rem] leading-3 md:text-subhead2">
          {{ selectedItem.name }}
        </h5>
      </div>
      <div class="flex gap-6 md:gap-10">
        <button
          class="transition duration-300 focus:text-black focus:outline-none focus:ring-black focus-visible:ring-2 focus-visible:ring-offset-4"
          :class="{ 'opacity-15': selectedIndex === 0 }"
          aria-label="Previous slide"
          :disabled="selectedIndex===0"
          @click="previousSlide"
        >
          <svg
            class="stroke-black"
            width="26"
            height="24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <title>Left arrow icon</title>
            <g fill="none" fill-rule="evenodd">
              <path
                d="M24.166 1.843L3.627 12.113l20.539 10.269V1.843z"
                stroke-width="2"
              ></path>
              <path fill="#D8D8D8" d="M.986.5h-1v22.775h1z"></path>
            </g>
          </svg></button
        ><button
          class="transition duration-300 focus:text-black focus:outline-none focus:ring-black focus-visible:ring-2 focus-visible:ring-offset-4 hover:opacity-50"
          aria-label="Next slide"
          :class="{ 'opacity-15': isNextButtonDisabled }"
          :disabled="isNextButtonDisabled"
          @click="nextSlide"
        >
          <svg
            class="stroke-black"
            width="26"
            height="24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <title>Right arrow icon</title>
            <g fill="none" fill-rule="evenodd">
              <path
                d="M1.528 1.843l20.538 10.27L1.528 22.382V1.843z"
                stroke-width="2"
              ></path>
              <path fill="#D8D8D8" d="M24.708.5h1v22.775h-1z"></path>
            </g>
          </svg>
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import DisplaySlide from "./DisplaySlide.vue";
export default {
  components: {
    DisplaySlide,
  },
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      selectedItem: this.$props.items[0],
      selectedIndex: 0,
      progressBarStep: "6.66667%"
    };
  },
  computed: {
    isNextButtonDisabled() {
      return this.selectedIndex === this.items.length - 1;
    }
  },
  methods: {
  nextSlide() {
    // Vérifie si on peut passer au slide suivant
    if (this.selectedIndex < this.$props.items.length - 1) {
      this.selectedIndex++;
      this.updateSelectedItem();
      this.updateProgressBar();
    }
  },
  previousSlide() {
    // Vérifie si on peut revenir au slide précédent
    if (this.selectedIndex > 0) {
      this.selectedIndex--;
      this.updateSelectedItem();
      this.updateProgressBar();
    }
  },
  updateSelectedItem() {
    // Met à jour l'élément sélectionné
    this.selectedItem = this.$props.items[this.selectedIndex];
  },
  updateProgressBar() {
    // Calcule et met à jour la largeur de la barre de progression
    const width = ((this.selectedIndex + 1) / this.$props.items.length) * 100;
    this.progressBarStep = `${width}%`; // Pas d'espace entre la valeur et '%'
  }
}
};
</script>

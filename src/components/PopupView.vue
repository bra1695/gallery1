<template>
  <div class="fixed inset-0 z-30 bg-black/85" style="opacity: 1"></div>
  <div class="fixed inset-0 z-50 grid place-items-center" style="opacity: 1">
    <div class="m-6 grid max-h-dvh grid-rows-[auto,1fr] gap-10">
      <div class="flex justify-end">
        <button
          @click="closePopup"
          class="text-[0.875rem] text-link1 uppercase text-white transition-opacity duration-300 hover:opacity-25 focus:text-black focus:outline-none focus:ring-black focus-visible:ring-2 focus-visible:ring-offset-4"
        >
          Close
        </button>
      </div>
      <div class="flex">
        <img
          class="h-full max-h-[85vh] w-auto object-cover"
          :src="image"
          :alt="name"
        />
      </div>
    </div>
  </div>
</template>
<script>
export default{
    props:{
        image:{
            type: String,
            required: true
        },
        name:{
            type: String,
            required: true
        }
    },
    methods: {
    closePopup() {
      this.$emit('close'); // Émet l'événement 'close' vers le parent
    },
  },
}
</script>

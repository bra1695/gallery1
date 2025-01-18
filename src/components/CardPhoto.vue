<template>
 <div 
 class="relative flex-grow flex items-stretch cursor-pointer group"
 >
 <img
        class="w-full h-auto object-cover"
        :src="item.images.thumbnail"
        :alt="item.name"
        :title="item.name"
      />
      <!-- Hover Overlay -->
      <div
        class="absolute inset-0 bg-black opacity-0 group-hover:opacity-50 transition-opacity duration-300"
      ></div>
      <!-- Caption -->
      <div
        class="absolute bottom-0 left-0 p-8 text-white lg:opacity-0 group-hover:opacity-100 transform translate-y-5 group-hover:translate-y-0 transition-all duration-300 ease-in-out"
      >
        <h2 class="text-xl text-custom-x-l mb-2 font-bold">{{ item.name }}</h2>
        <p class="text-custom-x-s opacity-70">{{ item.artist.name }}</p>
      </div>
 </div>
</template>
<script>
export default {
    props:{
        item:{
            type:Object,
            required: true
        }
    }
}
</script>
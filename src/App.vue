<template>
  <div>
    <div class="flex flex-row justify-between items-center p-4">
      <img :src="logo" alt="Logo" />
      <button
        @click="onChangeSlide()"
        class="cursor-pointer md:px-10 text-tertiary md:text-custom-xx-s tracking-[0.161em] font-bold text-custom-xxx-s hover:text-black"
      >
        {{ SliderText }}
      </button>
    </div>
    <MainListPhoto v-if="!startSlide" :items="items" />
    <SliderPhoto v-if="startSlide" :items="items"   />
  </div>
</template>
<script>
import jsonData from "@/assets/data.json";
import logo from "@/assets/images/galleria.png";
import MainListPhoto from "./components/MainListPhoto.vue";
import SliderPhoto from "./components/SliderPhoto.vue";
export default {
  components: {
    MainListPhoto,
    SliderPhoto
  },
  data() {
    return {
      logo,
      items: jsonData,
      startSlide: false,
      SliderText:"Start SlideShow"
    };
  },
  methods:{
    onChangeSlide(){
      this.startSlide=!this.startSlide;
      if(this.startSlide){
        this.SliderText="Stop SlideShow"
      }else{
        this.SliderText="Start SlideShow"
      }
    }
  }
};
</script>

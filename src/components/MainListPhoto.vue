<template>
  <main class="grid md:grid-cols-4 gap-8 py-8 md:p-10 px-6">
    <div class="flex flex-col gap-8">
      <CardPhoto
      v-for="(item, index) in firstColumn"
      :key="index"
      :item="item"

    >
    </CardPhoto>
    </div>
    <div class="flex flex-col gap-8">
      <CardPhoto
      v-for="(item, index) in secondColumn"
      :key="index"
      :item="item"
    >

    </CardPhoto>
    </div>
    <div class="flex flex-col gap-8">
      <CardPhoto
      v-for="(item, index) in thirdColumn"
      :key="index"
      :item="item"
    >
    </CardPhoto>
    </div>
    <div class="flex flex-col gap-8">
      
      <CardPhoto
      v-for="(item, index) in fourthColumn"
      :key="index"
      :item="item"
    >
    </CardPhoto>
    </div>

    <!-- Loop through gallery items -->

  </main>
</template>

<script>
import CardPhoto from './CardPhoto.vue';
export default {
  components:{
    CardPhoto
  },
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
  computed: {
    firstColumn() {
      // Filter items with indexes 0, 4, 8, 12
      return this.$props.items.filter((item, index) => index % 4 === 0);
    },
    secondColumn() {
      // Filter items with indexes 0, 4, 8, 12
      return this.$props.items.filter((item, index) => [1, 5, 9, 13].includes(index));
    },
    thirdColumn() {
      // Filter items with indexes 0, 4, 8, 12
      return this.$props.items.filter((item, index) => [2, 6, 12].includes(index));
    },
    fourthColumn() {
      // Filter items with indexes 0, 4, 8, 12
      return this.$props.items.filter((item, index) => [3, 7, 11,14].includes(index));
    },
  },
  methods: {
    getGridRowClass(index) {
      if (index % 4 === 0) return "md:row-span-2"; 
      return "md:row-span-1";
    },
  },
};
</script>
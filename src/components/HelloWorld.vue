<template>
  <section class="md:px-0 text-white py-28">
    <div class="flex justify-center align-center flex-wrap">
      <span
        class="text-sm sm:text-lg p-2 md:px-8 uppercase"
        v-for="(filter, index) in filters"
        :key="index + 'filter'"
      >
        {{ filter }}</span
      >
    </div>
    <div class="grid grid-cols-4 gap-6 md:gap-8 px-4 md:px-8 pt-6 md:px-24">
      <div
        :style="`height: ${height}px`"
        class="relative"
        v-for="(image, index) in images"
        :key="index + 'image'"
        :class="['col-span-' + image.size * 2, 'md:col-span-' + image.size]"
      >
        <img
          ref="square"
          :style="`height: ${height}px`"
          class="w-full block absolute transform object-cover -translate-x-1/2 -translate-y-1/2 top-1/2 left-1/2"
          :src="image.url"
        />
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      height: 50,
      filters: ["All", "Extension", "Lamination", "Nature", "Tinting"],
      images: [
        {
          url: "https://dummyimage.com/600x400/c21bc2/fff",
          size: 2,
        },
        {
          url: "https://dummyimage.com/600x400/4f114f/fff",
          size: 1,
        },
        {
          url: "https://dummyimage.com/600x400/5f53c9/fff",
          size: 1,
        },
        {
          url: "https://dummyimage.com/600x400/3022b3/fff",
          size: 1,
        },
        {
          url: "https://dummyimage.com/600x400/22b3a9/fff",
          size: 1,
        },
        {
          url: "https://dummyimage.com/600x400/127a73/fff",
          size: 2,
        },
        {
          url: "https://dummyimage.com/600x400/5ea100/fff",
          size: 2,
        },
        {
          url: "https://dummyimage.com/600x400/9fc418/fff",
          size: 1,
        },
        {
          url: "https://dummyimage.com/600x400/4f114f/fff",
          size: 1,
        },
      ],
    };
  },
  mounted() {
    this.$nextTick(function () {
      this.updateElementHeight();
    });
    window.addEventListener("resize", this.updateElementHeight);
  },
  methods: {
    updateElementHeight: function () {
      this.height = this.$refs.square[1].clientWidth;
    },
  },
};
</script>

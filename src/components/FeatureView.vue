<template>
  <div class="grid grid-cols-2 mt-10">
    <img class="md:h-fit" :src="myFeature.image" />
    <section class="ml-4">
      <h3 class="font-bold text-xl ml-4 text-[#943232]">
        {{ myFeature.name }}
      </h3>
      <p class="text-justify m-4 text-[#592913]">
        {{ myFeature.description }}
      </p>
    </section>
  </div>
</template>

<script>
export default {
  name: "FeatureView",
  props: ["myFeature"],
  data() {
    return {};
  },
  methods: {},
};
</script>

<style></style>

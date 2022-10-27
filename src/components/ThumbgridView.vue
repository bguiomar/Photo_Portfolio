<template>
  <div id="grid">
    <img
      class="w-full cursor-pointer rounded shadow transition duration-150 ease-in-out hover:opacity-75"
      v-for="project in allProjects"
      :key="project.id"
      :src="project.image"
      :alt="project.name"
      @click="showFeature(project.id)"
    />
  </div>
</template>

<script>
export default {
  name: "ThumbgridView",
  props: ["allProjects"],

  data() {
    return {};
  },

  methods: {
    showFeature(id) {
      //this up the information to the parent
      this.$emit("showFeatureProject", id);
    },
  },
};
</script>

<style>
#grid {
  display: grid;
  /* template = only for as many as are necessary to follow value to propert (1fr 1fr 1fr 1fr) */
  grid-template-columns: 1fr 1fr 1fr 1fr;
  /* auto = for this row and all the rows that follow */
  grid-auto-rows: 175px;
  gap: 20px;
  padding-top: 60px;
  padding-bottom: 80px;
}

#grid img {
  width: 100%;
  height: 100%;
  /* cover will clip image until it fits
    contain might leave white space if image with this ration doesn't fit*/
  object-fit: cover;
  cursor: pointer;
}
</style>

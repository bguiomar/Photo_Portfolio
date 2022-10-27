<template>
  <div>
    <feature-view :myFeature="featureProject" />
  </div>
  <div class="seperator"></div>
  <div>
    <!-- Insert props from Thumbs -->

    <thumbgrid-view
      :allProjects="allProjects"
      @showFeatureProject="showFeature"
    />
  </div>
</template>

<script>
import ThumbgridView from "./ThumbgridView.vue";
import FeatureView from "./FeatureView.vue";

export default {
  name: "UserView",
  props: ["allProjects", "featureProject"],
  data() {
    return {};
  },
  components: {
    FeatureView,
    ThumbgridView,
  },
  methods: {
    showFeature(id) {
      this.$emit("showFeatureProject", id);
    },
  },
};
</script>

<style></style>

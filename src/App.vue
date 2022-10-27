<template>
  <div class="container mx-auto mt-10 mb-5 h-screen">
    <nav class="flex justify-end mb-10 gap-3 px-2">
      <button
        @click="isAdmin = true"
        class="border rounded-md px-2 text-[#592913fb]"
        :class="{
          'text-[#dfa88efb] font-bold text-lg bg-[#592913fb] p-1': isAdmin,
        }"
      >
        ADMIN
      </button>
      <button
        @click="isAdmin = false"
        class="border rounded-md px-2 text-[#592913fb]"
        :class="{
          'text-[#dfa88efb] font-bold text-lg bg-[#592913fb] p-1': !isAdmin,
        }"
      >
        USER
      </button>
    </nav>
    <h1 class="flex text-4xl justify-center font-extrabold text-[#592913fb]">
      MY PORTFOLIO
    </h1>
    <section class="px-5">
      <AdminView v-if="isAdmin" @createProject="addProject" />

      <UserView
        v-else
        :allProjects="allProjects"
        :featureProject="theFeatureProject"
        @showFeatureProject="showFeature"
      />
    </section>
  </div>
</template>

<script>
import AdminView from "./components/AdminView.vue";
import UserView from "./components/UserView.vue";
import photos from "./photos.js";

export default {
  name: "app",

  components: {
    UserView,
    AdminView,
  },
  data() {
    return {
      isAdmin: false,
      allProjects: photos,
      theFeatureProject: photos[0],
    };
  },
  methods: {
    addProject(project) {
      // Give the new project a unique ID
      project.id = this.allProjects.length + 1;
      // Add the new project to 'allProjects'
      this.allProjects.push(project);
    },
    showFeature(id) {
      this.theFeatureProject = this.allProjects.find((p) => p.id === id);
    },
  },
};
</script>

<style>
body {
  font-family: "Azeret Mono", Courier, monospace;
  text-align: start;
  background-color: #eae3e1;
  color: #464443;
}
</style>

<template>
  <h2 class="font-bold text-xl text-center mt-5 text-[#592913fb]">
    ADD NEW PROJECT
  </h2>

  <div class="container mx-auto mt-10 flex flex-col text-[#592913fb]">
    <div class="mx-10">
      <form @submit.prevent="handleSubmit">
        <div class="flex gap-7">
          <div class="flex flex-col w-full">
            <p class="ml-5 font-semibold">Project Title</p>
            <input type="text" class="border border-amber-900" v-model="name" />
          </div>

          <div class="flex flex-col w-full">
            <p class="ml-5 font-semibold">Image URL</p>
            <input type="url" class="border border-amber-900" v-model="image" />
          </div>
        </div>

        <div class="flex flex-col mt-7">
          <p class="ml-5 font-semibold">Desctiption</p>
          <textarea
            type="text"
            class="border border-amber-900"
            v-model="description"
          />
        </div>
      </form>

      <div class="flex justify-center gap-3">
        <button
          type="submit"
          @click="handleSubmit"
          class="border border-amber-900 hover:bg-amber-700 bg-slate-50 mt-7 p-1 px-2 rounded-md text-[#592913fb]"
        >
          SUBMIT
        </button>
        <button
          type="reset"
          @click="reseatFormFields"
          class="border border-amber-900 hover:bg-amber-700 bg-slate-50 mt-7 p-1 px-2 rounded-md text-[#592913fb]"
        >
          RESET
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AdminView",
  data() {
    return {
      name: "",
      image: "",
      description: "",
    };
  },

  methods: {
    handleSubmit() {
      let newProject = {
        name: this.name,
        image: this.image,
        description: this.description,
      };
      this.$emit("createProject", newProject);
      //to reseat form:
      this.reseatFormFields();
    },

    // with this function we reset the form what you write at the web, but no the object information.
    reseatFormFields() {
      this.name = this.image = this.description = " ";
    },
  },
};
</script>

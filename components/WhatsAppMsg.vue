<template>
<div>


  <div class="card" style="width: 18rem">
    <img
      src="https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885__480.jpg"
      class="card-img-top"
      alt="https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885__480.jpg"
    />
    <div class="card-body">
      <h5 class="card-title">Card title</h5>
      <p class="card-text">
        Some quick example text to build on the card title and make up the bulk
        of the card's content.
      </p>
      <a href="#" class="btn btn-primary">Go somewhere</a>
    </div>
  </div>
  <NuxtLink to="/test">Home page</NuxtLink>
</div>
  
</template>
<script lang="ts">
import Vue from "vue";
export default Vue.extend({

  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start();
      setTimeout(() => this.$nuxt.$loading.finish(), 500);
    });
  },
  name: "WhatsAppMsg",
  data() {
    return {};
  },
});
</script>

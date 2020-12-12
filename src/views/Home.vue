<template>
  <div class="home">
    <gallery />
  </div>
</template>

<script>
import Gallery from "../components/Gallery.vue";
// @ is an alias to /src

export default {
  components: { Gallery },
  name: "Home"
};
</script>

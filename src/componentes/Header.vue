<template>
  <section class="src-componentes-header">
    <div id="header">
      <h1>
        The Great <br />
        <span id="colorDisplay">{{pickedColor}}</span>
        <br />
        Guessing Game
      </h1>
    </div>
  </section>
</template>

<script>
export default {
  name: "src-componentes-header",
  props: [pickedColor],
  mounted() {},
  data() {
    return {
      colorDisplay: document.getElementById("colorDisplay"),
      h1: document.querySelector("h1"),
      header: document.querySelector("#header"),
    };
  },
  methods: {},
  computed: {},
};
</script>

<style scoped>
</style>

<template>
  <section class="">
    <div id="container" v-bind="container">
      <div class="square" this.colors[0] @click="$emit('color',0)"></div>
      <div class="square" this.colors[1] @click="$emit('color',1)"></div>
      <div class="square" this.colors[2] @click="$emit('color',2)"></div>
      <div class="square" this.colors[3] @click="$emit('color',3)"></div>
      <div class="square" this.colors[4] @click="$emit('color',4)"></div>
      <div class="square" this.colors[5] @click="$emit('color',5)"></div>
    </div>
  </section>
</template>

<script>
export default {
  name: "src-componentes-container",
  props: [colores],
  mounted() {},
  data() {
    return {
      squares: document.querySelectorAll(".square"),
      pickedColor: this.colors[this.PickColor()],
      colors: this.colores,
      colorCount: 6,
    };
  },
  methods: {
    PickColor() {
            var quantity;
            if (this.isHard) {
                quantity = 6;
            } else {
                quantity = 3;
            }
            return Math.floor(Math.random() * quantity);
        },
  },
  computed: {},
};
</script>

<style scoped>
</style>
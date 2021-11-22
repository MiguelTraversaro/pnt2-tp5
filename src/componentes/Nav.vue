<template>
  <section class="">
    <div id="navigator">
      <button id="reset" @click="$emit('restart')">{{restartButton}}</button>
      <span id="message">{{mensaje}}</span>
      <button id="easy" @click="$emit('easy')">easy</button>
      <button id="hard" class="selected" @click="$emit('hard')">hard</button>
    </div>
  </section>
</template>

<script>
export default {
  name: "src-componentes-nav",
  props: [mensaje],
  mounted() {},
  data() {
    return {
      isHard: true,
      easyButton: document.querySelector("#easy"),
      hardButton: document.querySelector("#hard"),
      restartButton: document.querySelector("#reset"),
      messageDisplay: document.getElementById("message"),
    };
  },
  methods: {

  },
  computed: {
    
  },
};
</script>

<style scoped>
</style>

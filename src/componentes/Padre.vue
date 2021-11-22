<template>
    <div>
        <Header :pickedColor="pickedColor"/>
        <Nav :mensaje="mensaje" :restartButton="restartButton" @restart="restart" @easy="easyButton" @hard="hardButton"/>
        <Container :colors="colors" @color="correcto(pos)"/>
    </div>
</template>

<script>
import Header from "./Header.vue"
import Nav from "./Nav.vue"
import Container from "./Container.vue"

export default {
  name: "src-components-juego",
  props: [],
  components: {
      Header,Nav,Container
  },
  mounted() {
    this.start()
    this.colors = this.createNewColors();
    this.pickedColor = this.colors[this.pickColor()];
  },
  data() {
    return {
      colorCount: 6,
      isHard: true,
      colors: [],
      pickedColor: 0,
      mensaje: "",
      restartButton: "New Colors",
    };
  },
  methods: {
    start() {
      this.colors = this.createNewColors();
      console.log(this.colors);
    },
    createNewColors() {
      let resul = [];
      for (let i = 0; i < this.colorCount; i++) {
        resul.push(this.createRandomStringColor());
      }
      return resul;
    },
    createRandomStringColor() {
      return (
        "rgb(" +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ")"
      );
    },
    randomInt() {
      return Math.floor(Math.random() * 256);
    },
    pickColor() {
      let quantity;
      this.isHard ? (quantity = 6) : (quantity = 3);
      return Math.floor(Math.random() * quantity);
    },
    setAllColorsTo() {
      let squares = document.querySelectorAll(".square");
      for (let i = 0; i < this.colorCount; i++) {
        squares[i].style.backgroundColor = this.pickedColor;
      }
    },
    restart() {
      this.colors = this.createNewColors();
      this.pickedColor = this.colors[this.pickColor()];
      this.mensaje = "";
      this.restartButton = "New Colors";
    },
    easyButton() {
      if (this.isHard) {
        this.isHard = false;
        this.colorCount = 3;
        this.restart();
        document.querySelector("#hard").classList.remove("selected");
        document.querySelector("#easy").classList.add("selected");
      } else {
        this.restart();
      }
    },
    hardButton() {
      if (!this.isHard) {
        this.isHard = true;
        this.colorCount = 6;
        this.restart();
        document.querySelector("#easy").classList.remove("selected");
        document.querySelector("#hard").classList.add("selected");
      } else {
        this.restart();
      }
    },
    correcto(pos) {
      console.log(this.colors[pos]);
      if (this.colors[pos] == this.pickedColor) {
        this.setAllColorsTo(this.colors[pos]);
        this.mensaje = "You pick the right!";
        this.restartButton = "Play Again!";
      } else {
        document.querySelectorAll(".square")[pos].style.backgroundColor =
          "#fff";
        this.mensaje = "Try Again!";
      }
    },
  },
  computed: {},
};
</script>
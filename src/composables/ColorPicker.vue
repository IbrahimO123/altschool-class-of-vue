<template>
  <main>
    <h1>Color Picker Game</h1>
    <div>{{ message }}</div>
    <div class="button-container">
      <template v-for="(color, index) in colors" :key="color">
        <button :style="{ backgroundColor: color }" @click="matchColor(color)">
          {{ color }}
        </button>
      </template>
    </div>
  </main>
  <main>
    <h1>Instructions</h1>
    There are 5 colors listed below. You have to pick the correct color.
    <ul>
      <li>Select a color out of the colors listed out</li>
      <li>Select by clicking on a particular color</li>
      <li>Computer pick one already</li>
      <li>If what you picked matched what computer choosed</li>
      <li>You will get a congratulations message</li>
      <li>Otherwise you will try again !!!</li>
    </ul>
  </main>
</template>

<script>
import { ref, reactive } from "vue";
export default {
  name: "ColorPicker",
  setup() {
    const colors = reactive(["blue", "red", "green", "black", "orange"]);
    const message = ref("Pick a color...");
    const matchColor = (value) => {
      const randomNums = Math.floor(Math.random() * (colors.length - 1)) + 1;
      if (colors[randomNums] === value) {
        message.value = `You pick the correct color [answer: ${colors[randomNums]}]`;
      } else
        message.value = `You pick the wrong color [answer: ${colors[randomNums]}]`;

      const respond = setTimeout(
        () => (message.value = "Pick a color..."),
        2000
      );
      return clearInterval(() => respond);
    };

    return {
      message,
      colors,
      matchColor,
    };
  },
};
</script>

<style scoped>
main {
  width: 70vh;
  height: 70vh;
  display: flex;
  color:#000;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin: 10px 30px;
  padding: 10px 10px;
  background-color: #f1f1f1;
  border-radius: 10px;
}
.button-container {
  width: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
  margin: 20px;
}

button {
  width: 60px;
  height: 30px;
  padding: 3px;
  color: #fff;
  border: 1px solid #fff;
  border-radius: 5px;
}
@media screen and (max-width: 768px) {
  main {
    width: 100%;
    height: 100%;
    margin: 10px 0;
  }
}
</style>

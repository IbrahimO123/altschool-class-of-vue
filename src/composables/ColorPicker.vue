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
        return;
      } else
        message.value = `You pick the wrong color [answer: ${colors[randomNums]}]`;
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
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin: 0 auto;
  padding: 2px 5px;
  background-color: #f1f1f1;
  border-radius:10px;
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
</style>

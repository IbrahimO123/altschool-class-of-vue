<script>
import ColorPickerGame from "./components/ColorPickerGame.vue";
import Recap_01_02_2023 from "./components/Recap_01_02_2023.vue";
import ColorPicker from "./composables/ColorPicker.vue";

export default {
  components: { ColorPickerGame, Recap_01_02_2023, ColorPicker },
  data() {
    return {
      currentLesson: "color-picker-game",
    };
  },
};
</script>

<template>
  <!-- <ColorPickerGame v-if="currentLesson === 'color-picker-game'" />
  <Recap_01_02_2023 v-else /> -->
  <ColorPicker />
</template>

<style scoped></style>

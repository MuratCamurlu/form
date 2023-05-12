<template>
  <div @click="$emit('update:modelValue', !this.modelValue)">
    {{ modelValue ? "YES" : "NO" }}
  </div>
</template>
<script>
export default {
  name: "isAccept",
  props: ["modelValue"],
};
</script>
<style scoped></style>

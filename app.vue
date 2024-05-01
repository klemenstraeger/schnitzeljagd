<template>
  <div
    class="h-screen w-screen flex justify-center items-center bg-slate-600"
    :class="className"
  >
    <InputOtp
      v-model="value"
      class="h-16 text-2xl font-bold"
      integerOnly
      pt:input:class="h-full"
    />
  </div>
</template>
<script setup lang="ts">
import "primevue/resources/themes/aura-light-green/theme.css";
import JSConfetti from "js-confetti";

const jsConfetti = new JSConfetti();
import InputOtp from "primevue/inputotp";
const value = ref();
const className = computed(() => {
  console.log(value.value);

  if (value.value > 999) {
    if (value.value == 1234) {
      jsConfetti.addConfetti();
    }

    return {
      "!bg-red-600": value.value != 1234,
      "!bg-green-500": value.value == 1234,
    };
  }
});
</script>
<style>
.p-inputotp-input {
  height: 100%;
  width: 100%;
}
</style>

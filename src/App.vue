<script setup lang="ts">
import { ref } from 'vue'

const celsius = ref(0),
  fahrenheit = ref(32),
  kelvin = ref(273.15)

const celsiusToFahrenheit = () => {
  fahrenheit.value = round(+celsius.value * (9 / 5) + 32)
}

const celsiusToKelvin = () => {
  kelvin.value = round(+celsius.value + 273.15)
}

const kelvinToFahrenheit = () => {
  fahrenheit.value = round((+kelvin.value - 273.15) * (9 / 5) + 32)
}

const kelvinToCelsius = () => {
  celsius.value = round(+kelvin.value - 273.15)
}

const fahrenheitToCelsius = () => {
  celsius.value = round((+fahrenheit.value - 32) * (5 / 9))
}

const fahrenheitToKelvin = () => {
  kelvin.value = round((+fahrenheit.value - 32) * (5 / 9) + 273.15)
}

const round = (num: number) => parseFloat(num.toFixed(2))

const convertCelsius = () => {
  celsiusToFahrenheit()
  celsiusToKelvin()
}
const convertKelvin = () => {
  kelvinToCelsius()
  kelvinToFahrenheit()
}
const convertFahrenheit = () => {
  fahrenheitToCelsius()
  fahrenheitToKelvin()
}
</script>

<template>
  <main>
    <div class="temperature__item">
      <span>Celsius</span>
      <input v-model="celsius" type="range" orient="vertical" class="temperature__selector" min="-273.15" max="3500"
        @input="convertCelsius">
      <input v-model="celsius" type="number" @input="convertCelsius" min="-273.15" max="3500">
    </div>
    <div class="temperature__item">
      <span>Kelvin</span>
      <input v-model="kelvin" type="range" orient="vertical" class="temperature__selector" min="0" max="3773.15"
        @input="convertKelvin">
      <input v-model="kelvin" type="number" @input="convertKelvin" min="0" max="3773.15">
    </div>
    <div class="temperature__item">
      <span>Fahrenheit</span>
      <input v-model="fahrenheit" type="range" orient="vertical" class="temperature__selector" min="-459.67" max="6332"
        @input="convertFahrenheit">
      <input v-model="fahrenheit" type="number" @input="convertFahrenheit" min="-459.67" max="6332">
    </div>
  </main>
</template>

<style scoped>
main {
  display: flex;
  align-items: center;
  justify-content: space-between;
  column-gap: 1rem;
}

.temperature__item {
  display: flex;
  flex-direction: column;
  row-gap: 1rem;
}


input[type=range] {
  accent-color: #4F8C6F;
  background: transparent;
}

input[type=number] {
  background-color: transparent;
  border-radius: 5px;
  border: solid 1px rgba(255, 255, 255, 0.87);
  padding: 0.5rem 0.75rem;
  text-align: center;
  font-weight: 600;
  -moz-appearance: textfield;
}
</style>

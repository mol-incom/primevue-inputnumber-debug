<script setup>
import InputNumber from "primevue/inputnumber"
import {ref} from "vue"

const input = ref(0)
const emittedByAtInputValue = ref()
const emittedByAtInputFormattedValue = ref()
const emittedByAtUpdateModelValue = ref()

function onAtInput({value, formattedValue}) {
  console.log('onAtInput', {value, formattedValue, inputValue: input.value})
  emittedByAtInputValue.value = value
  emittedByAtInputFormattedValue.value = formattedValue
}

function onAtUpdateModelValue(value) {
  console.log('onAtUpdateModelValue', {value, inputValue: input.value})
  emittedByAtUpdateModelValue.value = value
}
</script>

<template>
  Input: <InputNumber v-model="input" style="width:100%" placeholder="here" @input="onAtInput" @update:modelValue="onAtUpdateModelValue"></InputNumber>
  <ul>
    <li>Number emitted by <code>@input</code> (.value): <code>{{emittedByAtInputValue}}</code></li>
    <li>Number emitted by <code>@input</code> (.formattedValue): <code>{{emittedByAtInputFormattedValue}}</code></li>
    <li>Number emitted by <code>@update:modelValue</code>: <code>{{emittedByAtUpdateModelValue}}</code></li>
  </ul>

</template>

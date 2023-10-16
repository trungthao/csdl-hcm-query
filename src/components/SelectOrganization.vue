<script setup>
import { computed, ref } from 'vue';
const props = defineProps(['modelValue'])
const emit = defineEmits(['update:modelValue', 'selectedOrg'])

const options = ref([
  {
    value: 'jack',
    label: 'Jack',
  },
  {
    value: 'lucy',
    label: 'Lucy',
  },
  {
    value: 'tom',
    label: 'Tom',
  },
]);

const value = computed({
  get() { return props.modelValue; },
  set(value) { emit('update:modelValue', value) }
})
const handleChange = value => {
  emit('selectedOrg', value);
};
const handleBlur = () => {
  console.log('blur');
};
const handleFocus = () => {
  console.log('focus');
};
const filterOption = (input, option) => {
  return option.value.toLowerCase().indexOf(input.toLowerCase()) >= 0;
};
</script>

<template>
  <a-select v-model:value="value" show-search placeholder="Select a person" style="width: 200px" :options="options"
    :filter-option="filterOption" @focus="handleFocus" @blur="handleBlur" @change="handleChange"></a-select>
</template>
<script setup lang="ts">
import { watch, ref, defineEmits } from 'vue'
import IconArrow from './icons/IconArrow.vue'
interface Props {
  value: string
}

const props = defineProps<Props>()
const inputValue = ref(props.value)
const emit = defineEmits(['updateIpAddress'])
const submit = () => {
  emit('updateIpAddress', inputValue.value)
}
watch(
  () => props.value,
  (newValue) => {
    inputValue.value = newValue
  }
)
</script>

<template>
  <div class="container-search">
    <input
      type="text"
      class="input"
      name="search-ip"
      id="ip-tracker"
      minlength="15"
      maxlength="15"
      v-model="inputValue"
      placeholder="Search for any IP address or domain"
      @keyup.enter="submit"
    />
    <button class="arrow-btn" @click="submit">
      <IconArrow />
    </button>
  </div>
</template>

<style scoped>
.container-search {
  margin: 1.5rem auto;
  max-width: 35rem;
  background-color: white;
  border-radius: var(--rounded);
  display: flex;
  justify-content: space-between;
}
.input {
  border-radius: var(--rounded) 0 0 var(--rounded);
  padding: 1rem;
  width: 100%;
  color: var(--primary);
  font-weight: 400;
  font-family: 'Rubik';
  border: 0;
}
.arrow-btn {
  border-radius: 0 var(--rounded) var(--rounded) 0;
  background-color: black;
  transition: 0.3s;
  padding: 1rem 1.25rem;
  border: 0;
  cursor: pointer;
  &:hover {
    background-color: var(--primary);
  }
  & svg {
    width: 10px;
  }
}
</style>

<template lang="pug">
.mb-4
  input.w-full.h-12.px-5(type="text" v-model="query" @input="$emit('onSearch', query)" placeholder="Поиск контактов..." class="w-full.px-2.py-1.border.border-gray-300.rounded")
</template>

<script setup lang="ts">
import { ref, watch } from 'vue'

const query = ref('')

const emit = defineEmits<{
    (e: 'onSearch', query: string): void
}>()

watch(query, (newVal) => {
    emit('onSearch', newVal)
})
</script>

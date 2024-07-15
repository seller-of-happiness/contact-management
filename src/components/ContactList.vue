<template lang="pug">
ul
  li(v-for="contact in contacts" :key="contact.id" class="mb-4")
    ContactItem(:contact="contact" @onEdit="$emit('onEdit', contact)" @onDelete="$emit('onDelete', contact.id)")
</template>

<script setup lang="ts">
import type { PropType } from 'vue'
import type { Contact } from '../types/types'
import ContactItem from './ContactItem.vue'

const props = defineProps<{
    contacts: Contact[]
}>()
</script>

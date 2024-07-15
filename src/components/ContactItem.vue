<template lang="pug">
.flex.items-center.justify-between.p-2.border.border-gray-300.rounded
  .contact-info
    p.font-semibold {{ contact.name }}
    p.text-gray-600 {{ contact.phone }}
    p.text-gray-600 {{ contact.email }}
  .contact-actions
    button.text-blue-500.mr-2(@click="$emit('onEdit', contact)") Редактировать
    button.text-red-500(@click="$emit('onDelete', contact.id)") Удалить
</template>

<script setup lang="ts">
import type { PropType } from 'vue'
import type { Contact } from '../types/types'

const props = defineProps<{
    contact: Contact
}>()
</script>

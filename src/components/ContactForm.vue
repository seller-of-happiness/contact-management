<template lang="pug">
form(@submit.prevent="handleSubmit")
  div.mb-4
    label.block.text-sm.font-medium.mb-1(for="name") Имя
    input#name.w-full.h-12.px-5(type="text" v-model="formData.name" class="w-full.px-2.py-1.border.border-gray-300.rounded" required)
  div.mb-4
    label.block.text-sm.font-medium.mb-1(for="phone") Телефон
    input#phone.w-full.h-12.px-5(type="tel" v-model="formData.phone" class="w-full.px-2.py-1.border.border-gray-300.rounded" required)
  div.mb-4
    label.block.text-sm.font-medium.mb-1(for="email") Email
    input#email.w-full.h-12.px-5(type="email" v-model="formData.email" class="w-full.px-2.py-1.border.border-gray-300.rounded" required)
  button.btn.bg-cyan-700.px-8.py-4.rounded-lg.mb-10(type="submit" class="bg-blue-500.text-white.px-4.py-2.rounded") {{ editingContact ? 'Сохранить' : 'Добавить' }}
</template>

<script setup lang="ts">
import { ref, watch } from 'vue'
import type { PropType } from 'vue'
import type { Contact } from '../types/types'

const props = defineProps<{
    editingContact: Contact | null
}>()

const emit = defineEmits<{
    (e: 'onAddContact', contact: Contact): void
    (e: 'onEditContact', contact: Contact): void
}>()

const formData = ref({
    id: Date.now(),
    name: '',
    phone: '',
    email: '',
})

watch(
    () => props.editingContact,
    (newVal) => {
        if (newVal) {
            formData.value = { ...newVal }
        } else {
            resetForm()
        }
    }
)

const handleSubmit = () => {
    if (props.editingContact) {
        emit('onEditContact', { ...formData.value })
    } else {
        formData.value.id = Date.now()
        emit('onAddContact', { ...formData.value })
    }
    resetForm()
}

const resetForm = () => {
    formData.value = {
        id: Date.now(),
        name: '',
        phone: '',
        email: '',
    }
}
</script>

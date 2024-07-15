<template lang="pug">
.container.mx-auto.p-4
  h1.text-2xl.font-bold.text-center.mb-5 Управление контактами
  SearchBar(@onSearch="handleSearch")
  ContactForm(@onAddContact="addContact" @onEditContact="editContact" :editingContact="editingContact")
  ContactList(:contacts="filteredContacts" @onEdit="startEditContact" @onDelete="deleteContact")
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import SearchBar from './components/SearchBar.vue'
import ContactForm from './components/ContactForm.vue'
import ContactList from './components/ContactList.vue'
import type { Contact } from './types/types'

const contacts = ref<Contact[]>(
    JSON.parse(localStorage.getItem('contacts') || '[]')
)
const searchQuery = ref('')
const editingContact = ref<Contact | null>(null)

const addContact = (contact: Contact) => {
    contacts.value.push(contact)
    saveContacts()
}

const editContact = (contact: Contact) => {
    const index = contacts.value.findIndex((c) => c.id === contact.id)
    if (index !== -1) {
        contacts.value[index] = contact
        saveContacts()
    }
    editingContact.value = null
}

const deleteContact = (id: number) => {
    contacts.value = contacts.value.filter((contact) => contact.id !== id)
    saveContacts()
}

const startEditContact = (contact: Contact) => {
    editingContact.value = { ...contact }
}

const handleSearch = (query: string) => {
    searchQuery.value = query
}

const filteredContacts = computed(() => {
    return contacts.value.filter((contact) =>
        contact.name.toLowerCase().includes(searchQuery.value.toLowerCase())
    )
})

const saveContacts = () => {
    localStorage.setItem('contacts', JSON.stringify(contacts.value))
}
</script>

<style scoped>
.container {
    max-width: 600px;
}
</style>

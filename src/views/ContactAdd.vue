<script setup>
    import { ref } from 'vue';
    import ContactForm from '@/components/ContactForm.vue';
    import contactsService from '@/services/contact.service';
    const message = ref('');
    const contact = ref({});
    async function onCreateContact(createdContact) {
        try {
            await contactsService.createContact(createdContact);
            message.value = 'Liên hệ được thêm thành công.';
        } catch (error) {
            console.log(error);
        }
    }
</script>
<template>
    <div class="page">
        <h4>Thêm Liên hệ</h4>
        <ContactForm
            :initial-contact="contact"
            @submit:contact="onCreateContact"
        />
        <p>{{ message }}</p>
    </div>
</template>
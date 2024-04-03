<template>
    <div class="page">
        <h4>Thêm mới Liên hệ</h4>
        <ContactForm
        :contact="contact"
        @submit:contact="addContact"
        />
        <p>{{ message }}</p>
    </div>
</template>
<script>
    import ContactForm from "@/components/ContactForm.vue";
    import ContactService from "@/services/contact.service";
    export default {
        components: {
            ContactForm,
        },
        data() {
            return {
                contact: {
                    // Khởi tạo một liên hệ trống để điền thông tin mới
                    name: "",
                    email: "",
                    phone: "",
                    // Các trường khác cũng có thể được thêm vào tùy theo yêu cầu của ứng dụng
                },
                message: "",
            };
        },
        methods: {
            async addContact(data) {
                try {
                    await ContactService.create(data);
                    this.message = "Liên hệ đã được thêm mới thành công.";
                } catch (error) {
                    console.log(error);
                }
            },
        },
    };
</script>

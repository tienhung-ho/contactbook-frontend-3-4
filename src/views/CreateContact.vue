<template>
  <div class="page">
    <h4>Tạo mới Liên hệ</h4>
    <ContactForm
      :contact="contact"
      @submit:contact="createContact"
    />
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
        name: "",
        email: "",
        address: "",
        phone: "",
        favorite: false,
      },
    };
  },
  methods: {
    async createContact(data) {
      try {
        await ContactService.create(data);
        this.$router.push({ name: "contactbook" });
      }
      catch(error) {
        console.log(error)
      }
    }
  },
};
</script>

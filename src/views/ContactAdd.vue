<template>
  <div class="page">
    <h4>Thêm Liên hệ</h4>
    <ContactForm @submit:contact="createContact" />
    <p>{{ message }}</p>
  </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";

export default {
  name: "AddContact",
  components: {
    ContactForm,
  },
  data() {
    return {
      message: "",
    };
  },
  methods: {
    async createContact(data) {
      try {
        await ContactService.create(data);
        alert("Liên hệ được thêm thành công.");
        this.$router.push({ name: "contactbook" });
      } catch (error) {
        console.log(error);
        this.message = "Đã xảy ra lỗi khi thêm liên hệ.";
      }
    },
  },
};
</script>

<style scoped>
.page {
  padding: 1rem;
}
h4 {
  margin-bottom: 1rem;
}
p {
  margin-top: 1rem;
  color: red;
}
</style>

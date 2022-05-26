<template>
  <div class="contactlist">
    <h1 class="header"> Contact list </h1>
    <ul>
      <Contact 
        v-for="contact in contacts"
        v-bind:contact="contact"
        v-on:search-contact="searchContact"
      />
    </ul>
  </div>
</template>

<script>
import Contact from "@/Contact.vue";

export default {
  props: ["contacts"],
  components: {
    Contact,
  },
  methods: {
      searchContact(id) {
          this.$emit('search-contact', id)
      }
  },
};
</script>

<style scoped>
.contactlist {
  width: 500px;
  height: 100%;
  border: 1px solid rgb(191, 191, 191);
  border-radius: 10px;
  padding: 10px;
}
.header {
  color: rgb(100, 100, 100);
  text-align: center;
  padding-bottom: 10px;
  border-bottom: 1px solid rgba(128, 128, 128, 0.3);
  margin-bottom: 20px;
}
</style>

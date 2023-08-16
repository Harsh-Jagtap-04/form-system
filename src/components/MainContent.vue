<template>
  <div class="main-content">
    <MultiStepForm v-if="showMultiStepForm" />
    <div v-else-if="showDefaultContent">
      <h1>Welcome to the Main Content</h1>
      <p>This is where your main content goes.</p>
    </div>
  </div>
</template>

<script>
import MultiStepForm from "@/components/MultiStepForm.vue";

export default {
  components: {
    MultiStepForm
  },
  props: {
    showMultiStepForm: Boolean
  },
  // Other properties and methods
};
</script>

<style scoped>
/* Main content styles */
.main-content {
  padding: 40px;
  background-color: #ffffff;
  box-shadow: 0 0 2px var(--grey-color-light);
  margin-top: 30px; /* Adjust this margin to prevent content from overlapping with the navbar */
  margin-left: 260px; /* Add margin to the left to account for the sidebar width */
}
</style>

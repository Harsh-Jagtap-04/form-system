<template>
  <div class="main-content">
    <MultiStepForm v-if="activeTab === 'apply_scheme'" />
    <DashboardPage v-else-if="activeTab === 'dashboard'" />
    <div v-else>
      <h1>Welcome to the Main Content</h1>
      <p>This is where your main content goes.</p>
    </div>
  </div>
</template>

<script>
import MultiStepForm from "@/components/MultiStepForm.vue";
import DashboardPage from "@/components/DashboardPage.vue";

export default {
  components: {
    MultiStepForm,
    DashboardPage
  },
  props: {
    showMultiStepForm: Boolean,
    activeTab: String
  }
};
</script>

<style scoped>
/* Main content styles */
.main-content {
  padding: 40px;
  background-color: #ffffff;
  box-shadow: 0 0 2px var(--grey-color-light);
  margin-top: 30px;
  margin-left: 260px;
}
</style>

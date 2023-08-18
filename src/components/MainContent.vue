<template>
  <div class="main-content">
    <MultiStepForm v-if="activeTab === 'apply_scheme'" />
    <DashboardPage v-else-if="activeTab === 'dashboard'" />
    <SchemeTable v-else-if="activeTab === 'schemes'"/>
    <ApplicationPage
      v-else-if="activeTab === 'applications'"
      @update:activeTab="updateActiveTab"
    />
    <EditFormPage v-else-if="activeTab === 'edit_form'" />

    
    <div v-else>
      <h1>Welcome to the Main Content</h1>
      <p>This is where your main content goes.</p>
    </div>
  </div>
</template>

<script>
import MultiStepForm from "@/components/MultiStepForm.vue";
import DashboardPage from "@/components/DashboardPage.vue";
import SchemeTable from "@/components/SchemeTable.vue";
import ApplicationPage from "@/components/ApplicationPage.vue";
import EditFormPage from "@/components/EditFormPage.vue";

export default {
  components: {
    MultiStepForm,
    DashboardPage,
    SchemeTable,
    ApplicationPage,
    EditFormPage
  },
  props: {
    showMultiStepForm: Boolean,
    activeTab: String
  },
  methods: {
    updateActiveTab(tabName) {
      this.$emit('update:activeTab', tabName); // Forward the event to App.vue
    },
  },
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

<template>
  <div class="dashboard">
    <div v-if="selectedOption === null" class="dashboard-options">
      <div class="dashboard-block" @click="selectOption('apply_scheme')">
        <div class="block-content">
          <h2>Apply for Scheme</h2>
        </div>
      </div>
      <div class="dashboard-block" @click="selectOption('schemes')">
        <div class="block-content">
          <h2>All Schemes</h2>
        </div>
      </div>
      <div class="dashboard-block" @click="selectOption('applications')">
        <div class="block-content">
          <h2>Applications</h2>
        </div>
      </div>
      <!-- Add more blocks for other options -->
    </div>
    <div v-else>
      <component :is="selectedOptionComponent" />
    </div>
  </div>
</template>


<script>
import MultiStepForm from "@/components/MultiStepForm.vue";
import SchemeTable from "@/components/SchemeTable.vue";
import ApplicationPage from "@/components/ApplicationPage.vue";
// ... (import other components)

export default {
  name: 'DashboardPage',
  components: {
    MultiStepForm,
    SchemeTable,
    ApplicationPage,
    // ... (other components)
  },
  data() {
    return {
      selectedOption: null
    };
  },
  computed: {
    selectedOptionComponent() {
      return this.selectedOption === 'apply_scheme'
        ? 'MultiStepForm'
        : this.selectedOption === 'schemes'
        ? 'SchemeTable'
        : this.selectedOption === 'applications'
        ? 'ApplicationPage'
        : null;
    }
  },
  methods: {
    selectOption(option) {
      this.selectedOption = option;
    }
  }
};
</script>

<style scoped>
.dashboard {
  padding: 40px;
  background-color: #ffffff;
  box-shadow: 0 0 2px var(--grey-color-light);

}

.dashboard-options {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  max-width: 800px;
  padding: 20px;
}

.dashboard-block {
  background-color: #ffffff;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 20px;
  cursor: pointer;
  transition: transform 0.2s, box-shadow 0.2s;
}

.dashboard-block:hover {
  transform: translateY(-5px);
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.1);
}

.block-content {
  text-align: center;
}

.block-content h2 {
  margin: 0;
  font-size: 18px;
  color: #333;
}
</style>

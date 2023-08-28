<template>
  <div>
    <NavBar />
    <SideBar :active-tab="activeTab" @tab-change="updateActiveTab" />
    
    <MainContent
      :active-tab="activeTab"
      :selected-option="selectedOption"
      @update:activeTab="updateActiveTab"
      @select-option="updateSelectedOption"
      @apply-for-scheme="handleApplyForScheme" 
    />

  </div>
</template>

<script>
import SideBar from "@/components/SideBar.vue";
import MainContent from "@/components/MainContent.vue";
import NavBar from "@/components/NavBar.vue";

export default {
  components: {
    SideBar,
    MainContent,
    NavBar
  },
  data() {
    return {
      activeTab: "dashboard", // Set the default active tab to "dashboard"
      selectedOption: null // Add this line
    };
  },
  methods: {
    updateActiveTab(tabName) {
      this.activeTab = tabName;
    },
    updateSelectedOption(option) {
    this.selectedOption = option;
  },
  handleApplyForScheme(scheme) {
      this.selectedOption = scheme; // Update the selectedOption with the scheme
    },
  }
};
</script>
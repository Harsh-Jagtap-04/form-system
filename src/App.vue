<template>
  <div>
    <NavBar />
    <SideBar :active-tab="activeTab" @tab-change="updateActiveTab" />
    <MainContent :active-tab="activeTab" @update:activeTab="updateActiveTab" />

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
      activeTab: "dashboard" // Set the default active tab to "dashboard"
    };
  },
  methods: {
    updateActiveTab(tabName) {
      this.activeTab = tabName;
    }
  }
};
</script>
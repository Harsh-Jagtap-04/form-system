<template>
    <div class="dashboard">
      <div v-if="selectedOption === null" class="dashboard-options">
        <div class="dashboard-block" @click="selectOption('user')">
          <div class="block-content">
            <h2>Add New User</h2>
          </div>
        </div>
        <div class="dashboard-block" @click="selectOption('gram')">
          <div class="block-content">
            <h2>Add Gram Panchayat</h2>
          </div>
        </div>
        <div class="dashboard-block" @click="selectOption('panchayat')">
          <div class="block-content">
            <h2>Add Panchayat Samiti</h2>
          </div>
        </div>
        <!-- Add more blocks for other options -->
      </div>

      <div v-else>
      <component :is="selectedOptionComponent" @go-back="goBackFromChild" />
    </div>

    </div>
  </template>
  
  
  <script>
  import RegisterNewUser from "@/components/RegisterNewUser.vue";
  import RegisterGP from "@/components/RegisterGP.vue";
  import RegisterPS from "@/components/RegisterPS.vue";
  // ... (import other components)
  
  export default {
    name: 'DashboardPage',
    components: {
        RegisterNewUser,
        RegisterGP,
        RegisterPS,

      // ... (other components)
    },
    data() {
      return {
        selectedOption: null
      };
    },
    computed: {
      selectedOptionComponent() {
        return this.selectedOption === 'user'
          ? 'RegisterNewUser'
          : this.selectedOption === 'gram'
          ? 'RegisterGP'
          : this.selectedOption === 'panchayat'
          ? 'RegisterPS'
          : null;
      }
    },
    methods: {
      selectOption(option) {
      this.selectedOption = option;
    },
    goBackFromChild() {
      this.selectedOption = null;
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
  
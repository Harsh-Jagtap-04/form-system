<template>
  <div>
    <navBar/>
    <SideBar @open-multi-step-form="openMultiStepForm" />
    <MainContent :show-multi-step-form="showMultiStepForm" />
  </div>
</template>

<script>
import SideBar from "@/components/SideBar.vue";
import MainContent from "@/components/MainContent.vue";
import NavBar from '@/components/NavBar.vue';

export default {
  components: {
    SideBar,
    MainContent,
    NavBar
  },
  data() {
    return {
      showMultiStepForm: false
    };
  },
  methods: {
    openMultiStepForm() {
      this.showMultiStepForm = true;
    }
  }
};
</script>

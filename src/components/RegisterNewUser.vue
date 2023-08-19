<template>
    <div class="form-container">
      <div id="multi-step-form-container" class="mt-5">
        <!-- Form Steps / Progress Bar -->

        <!-- Step Wise Form Content -->
        <form
          id="userRegistrationForm"
          name="userRegistrationForm"
          enctype="multipart/form-data"
          method="POST"
          @submit.prevent="submitForm"
        >
          <!-- Step 1 Content -->
          <section id="step-1" class="form-step" :class="{ 'd-none': currentStep !== 1 }">
            <h1 class="text-center">Register New User</h1>
            <div class="form-row">
              <!-- Left side: User Information -->
              <div class="form-group col-md-6">
                <label for="full-name">Full Name</label>
                <input type="text" id="full-name" class="form-control" />
              </div>
              <div class="form-group col">
                <label for="username">Username</label>
                <input type="text" id="username" class="form-control" />
              </div>
              <div class="form-group col">
                <label for="password">Password</label>
                <input type="password" id="password" class="form-control" />
              </div>
              <div class="form-group col">
                <label for="mobile-number">Mobile Number</label>
                <input type="tel" id="mobile-number" class="form-control" />
              </div>
              <div class="form-group col">
                <label for="email">Email</label>
                <input type="email" id="email" class="form-control" />
              </div>
              <div class="form-group col">
                <label for="description">Description</label>
                <textarea id="description" class="form-control"></textarea>
              </div>
            </div>
  
            <!-- Right side: Authority Checkboxes -->
            <div class="form-group col-md-6">
              <h2>Authority Names</h2>
              <div v-for="authority in authorities" :key="authority.id" class="form-group">
                <input
                  type="checkbox"
                  :id="`authority-${authority.id}`"
                  :value="authority.name"
                  class="form-check-input"
                />
                <label :for="`authority-${authority.id}`">{{ authority.name }}</label>
              </div>
            </div>
  
            <div class="button-container">
              <button class="button go-back-btn" @click="goBack">Go Back</button>
              <button class="button submit-btn" type="submit">Submit</button>
            </div>
          </section>
        </form>
      </div>

 

    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        currentStep: 1,
        authorities: [
          { id: 1, name: 'Demo Authority 1' },
          { id: 2, name: 'Demo Authority 2' },
          // ... Repeat for other authorities
        ]
      };
    },
    methods: {
      navigateToStep(stepNumber) {
        this.currentStep = stepNumber;
      },
      goBack() {
      this.$emit('go-back');
    },
      submitForm() {
        // Handle form submission
      }
    }
  };
  </script>
  

  
  <style scoped>

  .form-check {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
  .authority-checkboxes {
  flex: 1;
  padding-left: 2rem; /* Add spacing from the left side */
}
.authority-checkboxes h2 {
  margin-top: 0;
}
.authority-checkboxes .form-group {
  margin-bottom: 1rem;
}
  /* Your CSS styles here */
  .d-flex {
    display: flex;
    align-items: center;
    background: linear-gradient(135deg, #71b7e6, #9b59b6);
  }
  
  /* Align buttons to opposite sides */
  .justify-content-between {
    justify-content: space-between;
  }
  .form-row {
  display: flex;
  flex-direction: column;
  gap: 1rem; /* Vertical gap between form elements */
}
  .form-group {
  margin-bottom: 0.5rem;
}
  
  .form-group {
    /* display: flex;
    align-items: center; */
    margin-bottom: 1rem; /* Add some vertical spacing */
  }
  
  
  .full-name-label {
    display: flex;
    width: 50%; /* Adjust the width as needed */
    vertical-align: middle;
  }
  
  .file-input {
    display: inline-block;
    margin-top: 0.5rem;
  }
  
  
  /* Optional: Adjust form field widths if needed */
  .form-control {
    width: 100%;
    font-size: 20px;
  }
  
  
  h1 {
      text-align: center;
  }
  h2 {
      margin: 0;
  }
  #multi-step-form-container {
  width: 80%; /* Adjust width as needed */
}
  .form-container {
    background-color: #f9f8fd;
    padding: 2rem;
    border-radius: 10px;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);

  }
  .text-center {
      text-align: center;
  }
  .mx-auto {
      margin-left: auto;
      margin-right: auto;
  }
  .pl-0 {
      padding-left: 0;
  }
  .button {
      padding: 0.7rem 1.5rem;
      border: 1px solid #4361ee;
      background-color: #4361ee;
      color: #fff;
      border-radius: 5px;
      cursor: pointer;
  }
  .submit-btn {
      border: 1px solid #0e9594;
      background-color: #0e9594;
  }
  .mt-3 {
      margin-top: 2rem;
  }
  .d-none {
      display: none;
  }
  .form-step {
      border: 1px solid rgba(0, 0, 0, 0.1);
      border-radius: 20px;
      padding: 3rem;
  }
  .font-normal {
      font-weight: normal;
  }
  ul.form-stepper {
      counter-reset: inherit;
      margin-bottom: 3rem;
  }
  ul.form-stepper .form-stepper-circle {
      position: relative;
  }
  ul.form-stepper .form-stepper-circle span {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translateY(-50%) translateX(-50%);
  }
  .form-stepper-horizontal {
      position: relative;
      display: -webkit-box;
      display: -ms-flexbox;
      display: flex;
      -webkit-box-pack: justify;
      -ms-flex-pack: justify;
      justify-content: space-between;
  }
  ul.form-stepper > li:not(:last-of-type) {
      margin-bottom: 0.625rem;
      -webkit-transition: margin-bottom 0.4s;
      -o-transition: margin-bottom 0.4s;
      transition: margin-bottom 0.4s;
  }
  .form-stepper-horizontal > li:not(:last-of-type) {
      margin-bottom: 0 !important;
  }
  .form-stepper-horizontal li {
      position: relative;
      display: -webkit-box;
      display: -ms-flexbox;
      display: flex;
      -webkit-box-flex: 1;
      -ms-flex: 1;
      flex: 1;
      -webkit-box-align: start;
      -ms-flex-align: start;
      align-items: start;
      -webkit-transition: 0.5s;
      transition: 0.5s;
  }
  .form-stepper-horizontal li:not(:last-child):after {
      position: relative;
      -webkit-box-flex: 1;
      -ms-flex: 1;
      flex: 1;
      height: 1px;
      content: "";
      top: 32%;
  }
  .form-stepper-horizontal li:after {
      background-color: #dee2e6;
  }
  .form-stepper-horizontal li.form-stepper-completed:after {
      background-color: #4da3ff;
  }
  .form-stepper-horizontal li:last-child {
      flex: unset;
  }
  ul.form-stepper li a .form-stepper-circle {
      display: inline-block;
      width: 40px;
      height: 40px;
      margin-right: 0;
      line-height: 1.7rem;
      text-align: center;
      background: rgba(0, 0, 0, 0.38);
      border-radius: 50%;
  }
  .form-stepper .form-stepper-active .form-stepper-circle {
      background-color: #4361ee !important;
      color: #fff;
  }
  .form-stepper .form-stepper-active .label {
      color: #4361ee !important;
  }
  .form-stepper .form-stepper-active .form-stepper-circle:hover {
      background-color: #4361ee !important;
      color: #fff !important;
  }
  .form-stepper .form-stepper-unfinished .form-stepper-circle {
      background-color: #f8f7ff;
  }
  .form-stepper .form-stepper-completed .form-stepper-circle {
      background-color: #0e9594 !important;
      color: #fff;
  }
  .form-stepper .form-stepper-completed .label {
      color: #0e9594 !important;
  }
  .form-stepper .form-stepper-completed .form-stepper-circle:hover {
      background-color: #0e9594 !important;
      color: #fff !important;
  }
  .form-stepper .form-stepper-active span.text-muted {
      color: #fff !important;
  }
  .form-stepper .form-stepper-completed span.text-muted {
      color: #fff !important;
  }
  .form-stepper .label {
      font-size: 1rem;
      margin-top: 0.5rem;
  }
  .form-stepper a {
      cursor: default;
  }
  .form-stepper-active .form-stepper-circle {
    background-color: #3b2273 !important;
  }
  .button-container {
  display: flex;
  justify-content: center;
  margin-top: 2rem;
}

.button-container button {
  width: 100%; /* Make the button span the full width */
}
  </style>
  
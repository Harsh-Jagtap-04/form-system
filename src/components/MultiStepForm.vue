<template>
  <div class="form-container"> 
    <h1 class="text-center">Apply For Scheme</h1>
    <div id="multi-step-form-container" class="mt-5">
      <!-- Form Steps / Progress Bar -->
      <ul class="form-stepper form-stepper-horizontal text-center mx-auto pl-0">
        <!-- Step 1 -->
        <li :class="{'form-stepper-active': currentStep === 1, 'form-stepper-unfinished': currentStep !== 1}" step="1">
          <a class="mx-2">
            <span class="form-stepper-circle">
              <span>1</span>
            </span>
            <div class="label">Letter - A</div>           

          </a>
        </li>
        <!-- Step 2 -->
        <li :class="{'form-stepper-active': currentStep === 2, 'form-stepper-unfinished': currentStep !== 2}" step="2">
          <a class="mx-2">
            <span class="form-stepper-circle text-muted">
              <span>2</span>
            </span>
            <div class="label text-muted">Documents</div>
          </a>
        </li>
        <!-- Step 3 -->
        <li :class="{'form-stepper-active': currentStep === 3, 'form-stepper-unfinished': currentStep !== 3}" step="3">
          <a class="mx-2">
            <span class="form-stepper-circle text-muted">
              <span>3</span>
            </span>
            <div class="label text-muted">Verification</div>
          </a>
        </li>
      </ul>
      <!-- Step Wise Form Content -->
      <form
        id="userAccountSetupForm"
        name="userAccountSetupForm"
        enctype="multipart/form-data"
        method="POST"
        @submit.prevent="submitForm"
      >
        <!-- Step 1 Content -->
        <section id="step-1" class="form-step" :class="{ 'd-none': currentStep !== 1 }">
          <h2 class="font-normal">Account Basic Details</h2>
          <!-- Step 1 input fields -->
          
          <div class="mt-3">
            <div class="form-row">
    <div class="form-group col">
      <label class="full-name-label" for="first-name">First Name</label>
      <input type="text" id="first-name" class="form-control" />
    </div>
    <div class="form-group col">
      <label class="full-name-label" for="middle-name">Middle Name</label>
      <input type="text" id="middle-name" class="form-control" />
    </div>
    <div class="form-group col">
      <label class="full-name-label" for="last-name">Last Name</label>
      <input type="text" id="last-name" class="form-control" />
    </div>
  </div>
  <div class="form-row">
    <div class="form-group col">
      <label class="full-name-label" for="residing-at">Residing At</label>
      <input type="text" id="residing-at" class="form-control" />
    </div>
    <div class="form-group col">
      <label class="full-name-label" for="taluka">Taluka</label>
      <input type="text" id="taluka" class="form-control" />
    </div>
    <div class="form-group col">
      <label class="full-name-label" for="district">District</label>
      <input type="text" id="district" class="form-control" />
    </div>
  </div>
  </div>
  <div class="mt-3">
    <div class="form-group">
      <label class="full-name-label" for="poverty-line">Number of Poverty Line</label>
      <input type="number" id="poverty-line" class="form-control" />
    </div>
    <div class="form-group">
      <label class="full-name-label" for="group-number">Group Number</label>
      <input type="number" id="group-number" class="form-control" />
    </div>
    <div class="form-group">
      <label class="full-name-label"  for="total-land">Total Land</label>
      <input type="number" id="total-land" class="form-control" />
    </div>
  </div>
  <div class="mt-3">
    <div class="form-group">
      <label class="full-name-label" for="category">Category of Applicant</label>
      <select id="category" class="form-control">
        <option value="category-1">Category 1</option>
        <option value="category-2">Category 2</option>
        <option value="category-3">Category 3</option>
      </select>
    </div>
    <div class="form-group">
      <label class="full-name-label" for="categorized">Categorized</label>
      <input type="text" id="categorized" class="form-control" />
    </div>
    <div class="form-group">
      <label class="full-name-label" for="irrigation-facility">Irrigation Facility</label>
      <input type="text" id="irrigation-facility" class="form-control" />
    </div>
  </div>
  <div class="mt-3">
    <button class="button btn-navigate-form-step" type="button" @click="navigateToStep(2)">Next</button>
  </div>

        </section>
        <!-- Step 2 Content, default hidden on page load. -->
        <section id="step-2" class="form-step" :class="{ 'd-none': currentStep !== 2 }">
          <h2 class="font-normal">Documents</h2>
          <!-- Step 2 input fields -->
            <!-- File Uploads -->
  <div class="mt-3">
    <div class="form-group">
      <label class="full-name-label" for="extract-7-12">Online Extract of 7/12</label>
      <input type="file" id="extract-7-12" accept=".pdf, .jpg, .jpeg, .png" class="form-control" />
    </div>
    <div class="form-group">
      <label class="full-name-label" for="form-8a">Online Extract of Form 8A</label>
      <input type="file" id="form-8a" accept=".pdf, .jpg, .jpeg, .png" class="form-control" />
    </div>
    <div class="form-group">
      <label class="full-name-label" for="job-card">Job Card Copy</label>
      <input type="file" id="job-card" accept=".pdf, .jpg, .jpeg, .png" class="form-control" />
    </div>
    <div class="form-group">
      <label class="full-name-label" for="additional-land-affidavit">Additional Land Ownership Affidavit</label>
      <input type="file" id="additional-land-affidavit" accept=".pdf, .jpg, .jpeg, .png" class="form-control" />
    </div>
    <div class="form-group">
      <label class="full-name-label" for="water-usage-agreement">Water Usage Agreement</label>
      <input type="file" id="water-usage-agreement" accept=".pdf, .jpg, .jpeg, .png" class="form-control" />
    </div>
  </div>
          <div class="mt-3 d-flex justify-content-between">
    <button class="button btn-navigate-form-step" type="button" @click="navigateToStep(1)">Prev</button>
    <button class="button btn-navigate-form-step" type="button" @click="navigateToStep(3)">Next</button>
  </div>

  </section>
<!-- Step 3 Content -->
<section id="step-3" class="form-step" :class="{ 'd-none': currentStep !== 3 }">
  <h2 class="font-normal">Personal Details</h2>
  <!-- ... Previous fields ... -->

  <!-- Personal Details Inputs -->
  <div class="mt-3">
    <div class="form-group">
      <label for="aadhar-number">Aadhar Number</label>
      <input type="text" id="aadhar-number" class="form-control" />
    </div>
    <div class="form-group">
      <label for="mobile-number">Mobile Number</label>
      <input type="text" id="mobile-number" class="form-control" />
    </div>
    <div class="form-group">
      <label for="witness-1">Witness 1</label>
      <div class="witness-name-inputs">
        <input type="text" id="witness-1-names" class="form-control" placeholder="First Name, Middle Name, Last Name" />
      </div>
    </div>
    <div class="form-group">
      <label for="witness-2">Witness 2</label>
      <div class="witness-name-inputs">
        <input type="text" id="witness-2-names" class="form-control" placeholder="First Name, Middle Name, Last Name" />
      </div>
    </div>
  </div>

  <!-- File Uploads and Buttons -->
  <div class="mt-3">
    <!-- File uploads ... -->

    <div class="d-flex justify-content-between mt-3">
      <button class="button btn-navigate-form-step" type="button" @click="navigateToStep(2)">Prev</button>
      <button class="button submit-btn" type="submit">Save</button>
    </div>
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
      currentStep: 1
    };
  },
  methods: {
    navigateToStep(stepNumber) {
      this.currentStep = stepNumber;
    },
    submitForm() {
      // Handle form submission
    }
  }
};
</script>

<style scoped>
/* Your CSS styles here */
.d-flex {
  display: flex;
  align-items: center;
}

/* Align buttons to opposite sides */
.justify-content-between {
  justify-content: space-between;
}
.form-row {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1rem;
}
/*
.form-group {
  flex: 1;
  margin-right: 1rem;
}
*/
.form-group {
  display: flex;
  align-items: center;
  margin-bottom: 1rem; /* Add some vertical spacing */
}


.full-name-label {
  display: inline-block;
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
}


h1 {
    text-align: center;
}
h2 {
    margin: 0;
}
#multi-step-form-container {
    margin-top: 5rem;
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
    counter-reset: section;
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
</style>

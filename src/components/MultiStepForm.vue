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
          <h2 class="font-normal">User Basic Details</h2>
          <!-- Step 1 input fields -->
          
          <div class="mt-3">
            <div class="form-row">
    <div class="form-group col">
      <label class="full-name-label" for="first-name">First Name/प्रथम नाव
</label>
      <input type="text" id="ncharFirstName" class="form-control"  v-model="formData.ncharFirstName"/>
    </div>
    <div class="form-group col">
      <label class="full-name-label" for="middle-name">Middle Name/वडिलांचे नाव
</label>
      <input type="text" id="ncharMiddleName" class="form-control" v-model="formData.ncharMiddleName"/>
    </div>
    <div class="form-group col">
      <label class="full-name-label" for="last-name">Last Name/आडनाव</label>
      <input type="text" id="ncharLastName" class="form-control" v-model="formData.ncharLastName"/>
    </div>
  </div>
  
    <div class="form-group col">
      <label class="full-name-label" for="residing-at">Residing At/राहणार</label>
      <!-- <input type="text" id="residing-at" class="form-control" /> -->
      <textarea id="ncharResidingAt" class="form-control" v-model="formData.ncharResidingAt"></textarea>
    </div>
    <div class="form-row">
    <div class="form-group col">
      <label class="full-name-label" for="taluka">Taluka/तालुका</label>
      <input type="text" id="ncharTaluka" class="form-control" v-model="formData.ncharTaluka"/>
    </div>
    <div class="form-group col">
      <label class="full-name-label" for="district">District/जिल्हा</label>
      <input type="text" id="ncharDistrict" class="form-control" v-model="formData.ncharDistrict" />
    </div>
  </div>
<!-- </div> -->
<div class="form-row">
  <!-- <div class="mt-3"> -->
    <div class="form-group col">
      <label class="full-name-label" for="poverty-line">BPL Number/दारिद्र्य रेषेखालील क्रमांक</label>
      <input type="number" id="intBPLNumber" class="form-control" v-model="formData.intBPLNumber"/>
    </div>
    <div class="form-group col">
      <label class="full-name-label" for="group-number">Group Number/गट क्रमांक</label>
      <input type="number" id="intGroupNumber" class="form-control" v-model="formData.intGroupNumber" />
    </div>
  </div>
  </div>
    <div class="form-group">
      <label class="full-name-label"  for="total-land">Total Land/धारण केलेले एकुण क्षेत्र(आर)
</label>
      <input type="number" id="floatTotalLand" class="form-control" v-model="formData.floatTotalLand"/>
    </div>
  <!-- </div> -->
  <div class="mt-3">
    <div class="form-group">
      <label class="full-name-label" for="category">Category of Applicant/अर्जदाराचा संवर्ग</label>
      <select id="ncharCategory" class="form-control" v-model="formData.ncharCategory">
        <option value="category-1">Category 1</option>
        <option value="category-2">Category 2</option>
        <option value="category-3">Category 3</option>
      </select>
    </div>
    <div class="form-group">
      <label class="full-name-label" for="categorized">Categorized</label>
      <input type="text" id="ncharCategorized" class="form-control" v-model="formData.ncharCategorized"/>
    </div>
    <div class="form-group">
      <label class="full-name-label" for="irrigation-facility">Irrigation Facility/उपलब्ध असलेली सिंचन सुविधा
</label>
      <input type="text" id="ncharIrrigationFacility" class="form-control" v-model="formData.ncharIrrigationFacility"/>
    </div>
  </div>
  <div class="form-row">
    <div class="form-group col">
      <label class="full-name-label" for="form-Number">Form Number/प्राप्त अर्जाचा क्रमांक
</label>
      <input type="text" id="ncharFormNumber" class="form-control" v-model="formData.ncharFormNumber" />
    </div>
    <div class="form-group col">
      <label for="year">Year/वर्ष</label>
  <input type="number" id="intYear" class="form-control" min="1900" max="2099" step="1"  v-model="formData.intYear"/>

    </div>
  </div>
  <div class="mt-3">
    <button class="button btn-navigate-form-step" type="button" @click="navigateToStep(2)">Save and Next</button>
  </div>

        </section>
        <!-- Step 2 Content, default hidden on page load. -->
        <section id="step-2" class="form-step" :class="{ 'd-none': currentStep !== 2 }">
          <h2 class="font-normal">Documents</h2>
          <!-- Step 2 input fields -->
            <!-- File Uploads -->
  <div class="mt-3">
    <div class="form-group">
      <label class="full-name-label" for="extract-7-12">Online Transcript of 7/12 / ७/१२ चा ऑनलाईन उतारा</label>
      <input type="file" id="blobExtract712" accept=".pdf, .jpg, .jpeg, .png" class="form-control"  />
    </div>
    <div class="form-group">
      <label class="full-name-label" for="form-8a">Online Transcript of Form 8A</label>
      <input type="file" id="blobForm8A" accept=".pdf, .jpg, .jpeg, .png" class="form-control"  />
    </div>
    <div class="form-group">
      <label class="full-name-label" for="job-card">Copy of Job Card/ जॉबकार्ड ची प्रत</label>
      <input type="file" id="blobJobCard" accept=".pdf, .jpg, .jpeg, .png" class="form-control" />
    </div>
    <div class="form-group">
      <label class="full-name-label" for="additional-land-affidavit">Additional Land Ownership Affidavit/</label>
      <input type="file" id="blobAdditionalLandAffidavit" accept=".pdf, .jpg, .jpeg, .png" class="form-control" />
    </div>
    <div class="form-group">
      <label class="full-name-label" for="water-usage-agreement">Water Usage Agreement</label>
      <input type="file" id="blobWaterUsageAgreement" accept=".pdf, .jpg, .jpeg, .png" class="form-control"  />
    </div>
  </div>
          <div class="mt-3 d-flex justify-content-between">
    <button class="button btn-navigate-form-step" type="button" @click="navigateToStep(1)">Prev</button>
    <button class="button btn-navigate-form-step" type="button" @click="navigateToStep(3)">Save and Next</button>
  </div>

  </section>
<!-- Step 3 Content -->
<section id="step-3" class="form-step" :class="{ 'd-none': currentStep !== 3 }">
  <h2 class="font-normal">Personal Details</h2>
  <!-- ... Previous fields ... -->

  <!-- Personal Details Inputs -->
  <div class="mt-3">
    <div class="form-group">
      <label for="aadhar-number">Aadhar Number/आधार कार्ड नंबर
</label>
      <input type="text" id="ncharAadharNumber" class="form-control" v-model="formData.ncharAadharNumber" />
    </div>
    <div class="form-group">
      <label for="mobile-number">Mobile Number/मोबाईल नंबर</label>
      <input type="text" id="ncharMobileNumber" class="form-control" v-model="formData.ncharMobileNumber" />
    </div>
    <div class="form-group">
      <label for="witness-1">Witness 1/साक्षीदार 1</label>
      <div class="witness-name-inputs">
        <input type="text" id="ncharWitness1" class="form-control" placeholder="Enter your full Name " v-model="formData.ncharWitness1"/>
      </div>
    </div>
    <div class="form-group">
      <label for="witness-2">Witness 2/साक्षीदार 2</label>
      <div class="witness-name-inputs">
        <input type="text" id="ncharWitness2" class="form-control" placeholder="Enter your full Name"  v-model="formData.ncharWitness2"/>
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
import axios from 'axios';

export default {
  data() {
    return {
      currentStep: 1,
      formData: {
        ncharFirstName: '',
        ncharMiddleName: '',
        ncharLastName: '',
        ncharResidingAt: '',
        ncharTaluka: '',
        ncharDistrict: '',
        intBPLNumber: null,
        intGroupNumber: null,
        floatTotalLand: null,
        ncharCategory: '',
        ncharCategorized: '',
        ncharIrrigationFacility: '',
        ncharFormNumber: '',
        intYear: null,
        ncharAadharNumber: '',
        ncharMobileNumber: '',
        ncharWitness1: '',
        ncharWitness2: '',
        // Add fields for documents
        blobExtract712: null,
        blobForm8A: null,
        blobJobCard: null,
        blobAdditionalLandAffidavit: null,
        blobWaterUsageAgreement: null
      }
    };
  },
  methods: {
    navigateToStep(stepNumber) {
      this.currentStep = stepNumber;
    },

    submitForm() {
    const jsonData = {
      ncharFirstName: this.formData.ncharFirstName,
      ncharMiddleName: this.formData.ncharMiddleName,
      ncharLastName: this.formData.ncharLastName,
      ncharResidingAt: this.formData.ncharResidingAt,
      ncharTaluka: this.formData.ncharTaluka,
      ncharDistrict: this.formData.ncharDistrict,
      intBPLNumber: this.formData.intBPLNumber,
      intGroupNumber: this.formData.intGroupNumber,
      floatTotalLand: this.formData.floatTotalLand,
      ncharCategory: this.formData.ncharCategory,
      ncharCategorized: this.formData.ncharCategorized,
      ncharIrrigationFacility: this.formData.ncharIrrigationFacility,
      ncharFormNumber: this.formData.ncharFormNumber,
      intYear: this.formData.intYear,
      ncharAadharNumber: this.formData.ncharAadharNumber,
      ncharMobileNumber: this.formData.ncharMobileNumber,
      ncharWitness1: this.formData.ncharWitness1,
      ncharWitness2: this.formData.ncharWitness2,

      blobExtract712: this.formData.blobExtract712,
        blobForm8A: this.formData.blobForm8A,
        blobJobCard: this.formData.blobJobCard,
        blobAdditionalLandAffidavit: this.formData.blobAdditionalLandAffidavit,
        blobWaterUsageAgreement: this.formData.blobWaterUsageAgreement

    };

    axios
      .post('http://localhost:5555/saveApplication', jsonData, {
        headers: {
          'Content-Type': 'application/json'
        }
      })
      .then(response => {
          console.log('Application saved:', response.data);

      // Clear form fields
        this.formData.ncharFirstName = '';
        this.formData.ncharMiddleName = '';
        this.formData.ncharLastName = '';
        this.formData.ncharResidingAt = '';
        this.formData.ncharTaluka = '';
        this.formData.ncharDistrict = '';
        this.formData.intBPLNumber = null;
        this.formData.intGroupNumber = null;
        this.formData.floatTotalLand = null;
        this.formData.ncharCategory = '';
        this.formData.ncharCategorized = '';
        this.formData.ncharIrrigationFacility = '';
        this.formData.ncharFormNumber = '';
        this.formData.intYear = null;
        this.formData.ncharAadharNumber = '';
        this.formData.ncharMobileNumber = '';
        this.formData.ncharWitness1 = '';
        this.formData.ncharWitness2 = '';
        this.formData.blobExtract712 = null;
        this.formData.blobForm8A = null;
        this.formData.blobJobCard = null;
        this.formData.blobAdditionalLandAffidavit = null;
        this.formData.blobWaterUsageAgreement = null;
          // Reset step to 1
          this.currentStep = 1;

          // Show success message
          alert('Application submitted successfully');

        })
        .catch(error => {
          console.error('Error saving application:', error);
          // Handle error scenario, maybe show an error message
        });
    }
  }
};
</script>

<style scoped>
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
  justify-content: space-between;
  margin-bottom: 1rem;
}

.form-group {
  flex: 1;
  margin-right: 1rem;
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
    margin-top: 5rem;
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

</style>

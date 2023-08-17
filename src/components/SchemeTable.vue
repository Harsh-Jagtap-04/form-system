<template>
    <div class="scheme-table">
      <h1 class="text-center">Available Schemes</h1>
      <table class="table mt-5">
        <thead>
          <tr>
            <th>Scheme Name</th>
            <th>Category</th>
            <th>Eligibility</th>
            <th>Apply</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(scheme, index) in schemes" :key="index">
            <td>{{ scheme.name }}</td>
            <td>{{ scheme.category }}</td>
            <td>{{ scheme.eligibility }}</td>
            <td>
              <button class="button btn-apply" @click="applyForScheme(scheme)">Apply</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      schemes: Array, // Array of scheme objects
    },
    methods: {
      applyForScheme(scheme) {
        // Logic to handle applying for the selected scheme
        // You can emit an event or use a method from the parent component
      },
    },
  };
  </script>
  
  <style scoped>
  /* Your CSS styles here */
  .table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 2rem;
  }
  .table th,
  .table td {
    border: 1px solid #dee2e6;
    padding: 0.5rem 1rem;
    text-align: center;
  }
  .table th {
    background-color: #f8f7ff;
    font-weight: bold;
  }
  .button {
    padding: 0.5rem 1rem;
    border: 1px solid #4361ee;
    background-color: #4361ee;
    color: #fff;
    border-radius: 5px;
    cursor: pointer;
  }
  .btn-apply {
    background-color: #0e9594;
    border-color: #0e9594;
  }
  .text-center {
    text-align: center;
  }
  .mt-5 {
    margin-top: 3rem;
  }
  </style>
  
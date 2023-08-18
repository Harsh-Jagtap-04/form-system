<template>
    <div>
      <h1 class="text-center">Submitted Application Forms</h1>
      
      <!-- Search Bar -->
      <input
        v-model="searchQuery"
        placeholder="Search by Name"
        class="form-control mt-3"
      />
      
      <!-- Table -->
      <table class="table mt-3">
        <thead>
          <tr>
            <th>Name</th>
            <th>Category</th>
            <th>Actions</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(application, index) in filteredApplications" :key="index">
            <td>
              {{ application.firstName }} {{ application.middleName }} {{ application.lastName }}
            </td>
            <td>{{ application.category }}</td>
            <td>
              <button class="btn btn-primary" @click="editApplication(application)">Edit</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        searchQuery: '',
        applications: [
          // Dummy data (Replace with actual data)
          {
            firstName: 'John',
            middleName: 'Doe',
            lastName: 'Smith',
            category: 'Category 1',
            // ... other fields ...
          },
          // Add more application objects here
        ],
      };
    },
    computed: {
      filteredApplications() {
        return this.applications.filter(application =>
          this.matchesSearchQuery(application)
        );
      },
    },
    methods: {
      matchesSearchQuery(application) {
        const fullName = `${application.firstName} ${application.middleName} ${application.lastName}`;
        return fullName.toLowerCase().includes(this.searchQuery.toLowerCase());
      },
      editApplication(application) {
  console.log('Editing:', application);
  this.$emit('update:activeTab', 'edit_form');
},
    },
  };
  </script>
  
  <style scoped>
/* Table Styles */
.table {
  width: 100%;
  border-collapse: collapse;
  border-spacing: 0;
}

.table th,
.table td {
  padding: 0.75rem;
  border: 1px solid #dee2e6;
}

.table th {
  background-color: #f8f9fa;
  font-weight: bold;
  text-align: left;
}

/* Search Bar Styles */
.form-control {
  width: 100%;
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  line-height: 1.5;
  color: #495057;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}

/* Button Styles */
.btn {
  display: inline-block;
  font-weight: 400;
  color: #212529;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  user-select: none;
  border: 1px solid transparent;
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  line-height: 1.5;
  border-radius: 0.25rem;
  transition: color 0.15s ease-in-out, background-color 0.15s ease-in-out,
    border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}

.btn-primary {
  color: #fff;
  background-color: #007bff;
  border-color: #007bff;
}

.btn-primary:hover {
  color: #fff;
  background-color: #0056b3;
  border-color: #0056b3;
}

</style>

  
<template>
  <nav class="sidebar">
    <div class="menu_content">
      <ul class="menu_items">
        <!-- Menu item 1 -->
        <li class="item">
          <a href="#dashboard" class="nav_link submenu_item with-border" @click.prevent="openMultiStepForm('dashboard')" :class="{ active: activeTab === 'dashboard' }">
            <span class="navlink_icon">
              <i class="bx bx-home-alt"></i>
            </span>
            <span class="navlink center-text">Dashboard</span>
          </a>
        </li>
        <!-- Menu item 2 -->
        <li class="item">
          <a href="#apply_scheme" class="nav_link submenu_item with-border" @click.prevent="openMultiStepForm('apply_scheme')" :class="{ active: activeTab === 'apply_scheme' }">
            <span class="navlink_icon">
              <i class="bx bx-grid-alt"></i>
            </span>
            <span class="navlink center-text">Apply For scheme</span>
          </a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  methods: {
    openMultiStepForm(tabName) {
      this.$emit('tab-change', tabName);
    }
    // Other methods and properties
  }
};
</script>

<style>
/* Sidebar styles */
.sidebar {
  margin: 0;
  padding: 0;
  width: 260px; /* Increased sidebar width */
  background-color: #f1f1f1;
  position: fixed;
  height: 100%;
  overflow: auto;
}

/* Sidebar links */
/* Sidebar links */
.nav_link {
  display: block;
  color: black;
  padding: 16px;
  text-decoration: none;
  transition: background-color 0.3s, color 0.3s; /* Add smooth transition */
}

/* Active link */
.nav_link.active {
  background-color: #04AA6D;
  color: white;
}

/* Hover effect */
.nav_link:hover {
  background-color: #555;
  color: white;
}

/* Make sidebar responsive */
@media screen and (max-width: 700px) {
  .sidebar {
    width: 100%;
    height: auto;
    position: relative;
  }
  .nav_link {
    float: left;
  }
  div.content {
    margin-left: 0;
  }
}

@media screen and (max-width: 400px) {
  .nav_link {
    text-align: center;
    float: none;
  }
}
</style>
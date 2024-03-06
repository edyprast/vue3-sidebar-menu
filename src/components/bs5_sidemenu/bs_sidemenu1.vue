<script>
export default {
  data() {
    return {
      isSidebarExpanded: true,
    };
  },
  methods: {
    toggleSidebar() {
      this.isSidebarExpanded = !this.isSidebarExpanded;
    },
    handleWindowResize() {
      const sideBar = this.$refs.sideBar;
      const searchBtnIcon = this.$refs.searchBtnIcon;
      const searchForm = this.$refs.searchForm;

      if (window.innerWidth < 768) {
        // sideBar.classList.add('close');
        this.isSidebarExpanded = false;
      } else {
        // sideBar.classList.remove('close');
        this.isSidebarExpanded = true;
      }

      if (window.innerWidth > 576) {
        searchBtnIcon.classList.replace('bx-x', 'bx-search');
        // searchForm.classList.remove('show');
        this.isSidebarExpanded = true;
      }
    },
  },
  mounted() {
    window.addEventListener('resize', this.handleWindowResize);
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.handleWindowResize);
  },
};
</script>

<template>
  <div class="wrapper">
    <aside id="sidebar" ref="sideBar" :class="{ expand: isSidebarExpanded }">
      <div class="d-flex">
        <a href="#" class="logo">
          <i class='bx bx-code-alt'></i>
          <div class="logo-name"><span>Asmr</span>Prog</div>
        </a>
      </div>
      <ul class="sidebar-nav">
        <li class="sidebar-item">
          <a class="sidebar-link" href="#">
            <i class="lni lni-user"></i>
            <span>Profile</span>
          </a>
        </li>
        <li class="sidebar-item">
          <a class="sidebar-link" href="#">
            <i class="lni lni-agenda"></i>
            <span>Task</span>
          </a>
        </li>
        <li class="sidebar-item">
          <a aria-controls="auth" aria-expanded="false" class="sidebar-link collapsed has-dropdown"
            data-bs-target="#auth" data-bs-toggle="collapse" href="#">
            <i class="lni lni-protection"></i>
            <span>Auth</span>
          </a>
          <ul id="auth" class="sidebar-dropdown list-unstyled collapse" data-bs-parent="#sidebar">
            <li class="sidebar-item">
              <a class="sidebar-link" href="#">Login</a>
            </li>
            <li class="sidebar-item">
              <a class="sidebar-link" href="#">Register</a>
            </li>
          </ul>
        </li>
        <li class="sidebar-item">
          <a aria-controls="multi" aria-expanded="false" class="sidebar-link collapsed has-dropdown"
            data-bs-target="#multi" data-bs-toggle="collapse" href="#">
            <i class="lni lni-layout"></i>
            <span>Multi Level</span>
          </a>
          <ul id="multi" class="sidebar-dropdown list-unstyled collapse" data-bs-parent="#sidebar">
            <li class="sidebar-item">
              <a aria-controls="multi-two" aria-expanded="false" class="sidebar-link collapsed"
                data-bs-target="#multi-two" data-bs-toggle="collapse" href="#">
                Two Links
              </a>
              <ul id="multi-two" class="sidebar-dropdown list-unstyled collapse">
                <li class="sidebar-item">
                  <a class="sidebar-link" href="#">Link 1</a>
                </li>
                <li class="sidebar-item">
                  <a class="sidebar-link" href="#">Link 2</a>
                </li>
              </ul>
            </li>
          </ul>
        </li>
        <li class="sidebar-item">
          <a class="sidebar-link" href="#">
            <i class="lni lni-popup"></i>
            <span>Notification</span>
          </a>
        </li>
        <li class="sidebar-item">
          <a class="sidebar-link" href="#">
            <i class="lni lni-cog"></i>
            <span>Setting</span>
          </a>
        </li>
      </ul>
      <div class="sidebar-footer">
        <a class="sidebar-link" href="#">
          <i class="lni lni-exit"></i>
          <span>Logout</span>
        </a>
      </div>
    </aside>
    <div class="content">
      <nav>
        <i class='bx bx-menu' @click="toggleSidebar"></i>
        <form ref="searchForm" action="#">
          <div class="form-input">
            <input placeholder="Search..." type="search">
            <button ref="searchBtnIcon" class="search-btn" type="submit"><i ref="searchBtnIcon"
                class='bx bx-search'></i></button>
          </div>
        </form>
        <input id="theme-toggle" v-model="isDarkMode" hidden type="checkbox" @change="toggleTheme">
        <label class="theme-toggle" for="theme-toggle"></label>
        <a class="notif" href="#">
          <i class='bx bx-bell'></i>
          <span class="count">12</span>
        </a>
        <!-- <a class="profile" href="#">
          <img src="../../assets/images/logo.png">
        </a> -->
        <div class="dropdown">
          <div class="profile dropdown-toggle" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
            <img src="../../assets/images/logo.png">
          </div>
          <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
            <li><a class="dropdown-item" href="#"><i class="lni lni-swift"></i> <span class="ms-2">Action</span></a></li>
            <li><a class="dropdown-item" href="#"><i class="lni lni-t-shirt"></i> <span class="ms-2">Another action</span></a></li>
            <li><a class="dropdown-item" href="#"><i class="lni lni-sun"></i><span class="ms-2">Something else here</span></a></li>
          </ul>
        </div>
      </nav>
      <div class="breadcrumbs mt-4 ps-4">
        <ol class="breadcrumb">
          <li class="breadcrumb-item"><a href="#">Home</a></li>
          <li class="breadcrumb-item"><a href="#">Library</a></li>
          <li class="breadcrumb-item active" aria-current="page">Data</li>
        </ol>
      </div>
      <main class="mt-2 ps-3 pe-3">

        <div class="row">
          <div class="col">
            <div class="card mt-2">
              <div class="card-body">
                <h5 class="card-title">Card title</h5>
                <h6 class="card-subtitle mb-2 text-muted">Card subtitle</h6>
                <p class="card-text">Some quick example text to build on the card title and make up the bulk of the
                  card's content.</p>
                <a class="card-link" href="#">Card link</a>
                <a class="card-link" href="#">Another link</a>
              </div>
            </div>
          </div>

          <div class="col">
            <div class="card mt-2">
              <div class="card-body">
                <h5 class="card-title">Card title</h5>
                <h6 class="card-subtitle mb-2 text-muted">Card subtitle</h6>
                <p class="card-text">Some quick example text to build on the card title and make up the bulk of the
                  card's content.</p>
                <a class="card-link" href="#">Card link</a>
                <a class="card-link" href="#">Another link</a>
              </div>
            </div>
          </div>

          <div class="col mt-2">
            <div class="card">
              <div class="card-body">
                <h5 class="card-title">Card title</h5>
                <h6 class="card-subtitle mb-2 text-muted">Card subtitle</h6>
                <p class="card-text">Some quick example text to build on the card title and make up the bulk of the
                  card's content.</p>
                <a class="card-link" href="#">Card link</a>
                <a class="card-link" href="#">Another link</a>
              </div>
            </div>
          </div>

        </div>

        <div class="row mt-2">
          <div class="col mt-2">
            <div class="card">
              <div class="card-body">
                <h5 class="card-title">Card title</h5>
                <h6 class="card-subtitle mb-2 text-muted">Card subtitle</h6>
                <p class="card-text">Some quick example text to build on the card title and make up the bulk of the
                  card's content.</p>
                <a class="card-link" href="#">Card link</a>
                <a class="card-link" href="#">Another link</a>
              </div>
            </div>
          </div>

          <div class="col mt-2">
            <div class="card">
              <div class="card-body">
                <h5 class="card-title">Card title</h5>
                <h6 class="card-subtitle mb-2 text-muted">Card subtitle</h6>
                <p class="card-text">Some quick example text to build on the card title and make up the bulk of the
                  card's content.</p>
                <a class="card-link" href="#">Card link</a>
                <a class="card-link" href="#">Another link</a>
              </div>
            </div>
          </div>

        </div>

      </main>
    </div>
  </div>
</template>

<style>
@import "../../assets/custom_css/style_bs5_sidemenu.css";
</style>
<template>
  <nav class="navbar fixed">
    <div class="container-fluid d-flex align-items-center justify-content-center">
      <span class="navbar-brand mb-0 h1 text-center">
        Selamat Datang Di Tabungan {{ judul }}
      </span>
    </div>
  </nav>
</template>

<script setup>
defineProps({
  judul: String
})
</script>

<style scoped>
.navbar {
  background: #1A9EA7;
  height: 15vh;
}

.navbar-brand {
  color: white;
  font-size: 40px;
  font-weight: bold;
  text-align: center;
}

@media (max-width: 768px) {
  .navbar {
    height: 10vh; /* Kurangi tinggi navbar untuk layar kecil */
  }

  .navbar-brand {
    font-size: 24px; /* Ukuran font lebih kecil */
  }
}

@media (max-width: 576px) {
  .navbar {
    height: 8vh; /* Tinggi lebih kecil untuk layar HP */
  }

  .navbar-brand {
    font-size: 18px; /* Ukuran font lebih kecil lagi */
  }
}
</style>

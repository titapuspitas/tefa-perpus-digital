<template>
    <div class="container-fluid">
      <div class="row my-5 d-flex justify-content-evenly">
        <div class="col-lg-6 box">
          <NuxtLink to="/pengunjung/tambah">
            <div class="card bg-pengunjung rounded-5">
              <div class="card-body">
                <h2>Pengunjung</h2>
              </div>
            </div>
          </NuxtLink>
      </div>
      <div class="col-lg-6 box">
        <NuxtLink to="/buku">
          <div class="card bg-buku rounded-5">
            <div class="card-body">
              <h2>Buku</h2>
            </div>
          </div>
        </NuxtLink>
      </div>
    </div>

    <div class="statistik">
      <h1>STATISTIK</h1>
    </div>
    <div class="row my-5 d-flex justify-content-evenly">
      <div class="col-lg-6 box">
        <NuxtLink to="/pengunjung">
          <div class="card b2 rounded-5">
            <div class="card-body text">
              <h2 class="pt-4">
                <span class="no">{{ jmlh_pengunjung }}</span
                  >Pengunjung
                </h2>
              </div>
            </div>
        </NuxtLink>
      </div>
      <div class="col-lg-6 box">
        <NuxtLink to="/buku">
          <div class="card b3 rounded-5">
            <div class="card-body text">
              <h2 class="pt-4">
                <span class="no">{{ jmlh_buku }}</span
                  >Buku
                </h2>
              </div>
            </div>
          </NuxtLink>
        </div>
      </div>
      <div class="container">
        <div class="row">
          <Statistik />
        </div>
      </div>
    </div>
  </template>

<script setup>
const supabase = useSupabaseClient();
const jmlh_pengunjung = ref(0);
const jmlh_buku = ref(0);

async function getjmlh_pengunjung() {
  const { error, data, count } = await supabase.from("pengunjung").select("*", { count: "exact" });
  if (count) jmlh_pengunjung.value = count;
}

async function getjmlh_buku() {
  const { error, data, count } = await supabase.from("buku").select("*", { count: "exact" });
  if (count) jmlh_buku.value = count;
}

onMounted(() => {
  getjmlh_pengunjung();
  getjmlh_buku();
});

useHead({ title: "Home / PERPUSTAKAAN DIGITAL" });
</script>

<style scoped>
.card {
  height: 250px;
}
.card.bg-pengunjung {
  background-image: url("../assets/img/bg-hom-pengunjung.jpeg");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  color: black;
}
.card.bg-buku {
  background: url("../assets/img/bg-home-perpus.jpeg") no-repeat center center;
  background-size: cover;
  color: black;
}
.statistik {
  color: rgb(181, 74, 74);
  margin-left: 50px;
}
.box {
  width: 45%;
}
.box a {
  text-decoration: none;
}
.b2 {
  background-color: #ffd0d0f2;
  color: rgba(0, 0, 0, 0.778);
}
.b3 {
  background-color: rgba(181, 74, 74, 0.761);
  color: black;
}
.text {
  display: flex;
  justify-content: center;
  align-items: center;
}
.no {
  font-size: 70px;
}
</style>

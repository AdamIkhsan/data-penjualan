<template>
  <div>
    <div class="col-md-6 m-auto p-3">
      <h1 class="text-center">Isi Data Barang</h1>
      <form @submit.prevent="simpan()">
        <input
          v-model="nama_barang"
          placeholder="nama barang"
          class="form-control"
        />
        <br />
        <input
          v-model="jumlah_barang"
          placeholder="jumlah barang"
          class="form-control"
        />
        <br />
        <input
          v-model="harga_barang"
          placeholder="harga barang"
          class="form-control"
        />
        <br />
        <button type="submit" class="btn btn-info text-white me-3">
          Kirim
        </button>
        <NuxtLink to="/" class="btn btn-dark text-decoration-none text-light"
          >Kembali</NuxtLink
        >
      </form>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();
const nama_barang = ref();
const jumlah_barang = ref();
const harga_barang = ref();

async function simpan() {
  await supabase.from("databarang").insert({
    nama_barang: nama_barang.value,
    jumlah_barang: jumlah_barang.value,
    harga_barang: harga_barang.value,
  });
  const router = useRouter();
  router.push("/");
}
</script>
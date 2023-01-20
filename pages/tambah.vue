<template>
  <div>
    <h1>Isi Data Barang</h1>
    <form @submit.prevent="simpan()">
      <input v-model="nama_barang" placeholder="nama_barang" /> <br />
      <input v-model="jumlah_barang" placeholder="jumlah_barang" /> <br />
      <input v-model="harga_barang" placeholder="harga_barang" /> <br />
      <button type="submit">Kirim</button>
      <NuxtLink to="/">Kembali</NuxtLink>
    </form>
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
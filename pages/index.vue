<template>
  <div>
    <h2>Data Barang</h2>
    <NuxtLink to="/tambah">Isi Data Barang</NuxtLink>
    <table border="1" width="100%">
      <thead>
        <tr>
          <th>#</th>
          <th>NAMA BARANG</th>
          <th>JUMLAH BARANG</th>
          <th>HARGA BARANG</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="visitor in datas" :key="visitor.id">
          <td>{{ visitor.id }}</td>
          <td>{{ visitor.nama_barang }}</td>
          <td>{{ visitor.jumlah_barang }}</td>
          <td>{{ visitor.harga_barang }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>


<script setup>
const supabase = useSupabaseClient();
const datas = ref([]);

async function getData() {
  const { data, error } = await supabase.from("databarang").select();
  datas.value = data;
}

onMounted(() => {
  getData();
});
</script>
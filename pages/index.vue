<template>
  <div class="container">
    <h2 class="text-center">Data Barang</h2>
    <NuxtLink to="/tambah" class="btn btn-primary text-decoration-none mb-3"
      >Isi Data Barang</NuxtLink
    >
    <table border="1" width="100%" class="table bg-dark text-light">
      <thead>
        <tr>
          <th>#</th>
          <th>NAMA BARANG</th>
          <th>JUMLAH BARANG</th>
          <th>HARGA BARANG</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(visitor, i) in datas" :key="visitor.id">
          <td>{{ i }}</td>
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
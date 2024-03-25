<template>
  <div>
    <h1>{{ buku.judul }}</h1>
    <span v-if="buku.cover"><img :src="buku.cover" :alt="buku.judul"></span>
    <span v-else><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Placeholder_view_vector.svg/681px-Placeholder_view_vector.svg.png" :alt="buku.judul"></span>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()
const route = useRoute()
const buku = ref([])

const getBukuById = async () => {
  const { data, error } = await supabase.from('buku').select(`*, kategori(*)`)
  .eq('id', route.params.id)
  if(data) buku.value = data[0]
}

onMounted(() => {
  getBukuById()
})
</script>
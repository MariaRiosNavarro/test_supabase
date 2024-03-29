<script setup>
import { createClient } from "@supabase/supabase-js";
const supabase = createClient(
  "https://cdtkmwduiolmrwydhfxe.supabase.co",
  "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImNkdGttd2R1aW9sbXJ3eWRoZnhlIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MTE3MTg0MTQsImV4cCI6MjAyNzI5NDQxNH0.RQMiIVQDlWcT2DtEJtmHwb-jJTqwoO200bwxeXVAWRE"
);
const countries = ref([]);

async function getCountries() {
  const { data } = await supabase.from("countries").select();
  countries.value = data;
}

onMounted(() => {
  getCountries();
});
</script>

<template>
  <ul>
    <li v-for="country in countries" :key="country.id">{{ country.name }}</li>
  </ul>
</template>

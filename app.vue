<script setup>
import { ref, onMounted, provide } from "vue";
// import { createClient } from "@supabase/supabase-js";
import { supabase } from "./utils/supabase.ts";

const todos = ref([]);


const getTodos = async () => {
  try {
    const { data, error } = await supabase
      .from("test_table")
      .select("headline");
    if (error) {
      throw error;
    }

    todos.value = data;
    console.log(data);
  } catch (error) {
    console.error("Error fetching todos:", error.message);
    console.log(error);
  }
};

onMounted(() => {
  getTodos();
});

provide("supabaseClient", supabase);
</script>

<template>
  <h1>test</h1>
</template>

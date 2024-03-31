<script setup>
import { ref, onMounted, provide } from "vue";
// import { createClient } from "@supabase/supabase-js";
import { supabase } from "./utils/supabase.ts";

const testData = ref([]);

const getTestData = async () => {
  try {
    const { data, error } = await supabase.from("test_table").select();
    if (error) {
      throw error;
    }
    testData.value = data;
    console.log(data);
  } catch (error) {
    console.error("Error fetching todos:", error.message);
    console.log(error);
  }
};

onMounted(() => {
  getTestData();
});

provide("supabaseClient", supabase);
</script>

<template>
  <h1>TEST HEADLINE</h1>
  <div>
    <!-- Nur jeder Object -->
    <div>
      <ul>
        <li v-for="dataItem in testData" :key="dataItem.id">
          {{ dataItem }}
        </li>
      </ul>
    </div>

    <!-- Von jeder Object, jeder Value -->
    <div>
      <ul>
        <li v-for="dataItem in testData" :key="dataItem.id">
          <ul>
            <!-- Map durch alle values -->
            <li v-for="value in Object.values(dataItem)" :key="value">
              {{ value }}
            </li>
          </ul>
        </li>
      </ul>
    </div>

    <!-- table -->
    <div>
      <table v-if="testData.length">
        <thead>
          <tr>
            <th v-for="(value, key) in testData[0]" :key="key">
              {{ key }}
            </th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="dataItem in testData" :key="dataItem.id">
            <td v-for="value in Object.values(dataItem)" :key="value">
              {{ value }}
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

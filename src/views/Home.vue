<script setup>
/**
 * Imports
 */
  import { ref } from "vue";
  import Button from "../components/Button.vue"

/**
 * Props
 */
//   const titles = ref([
//     {
//       title: "Invoicer",
//       location: "/invoice"
//     },

//     {
//       title: "Payload"
//     },

//     {
//       title: "Verifier"
//     }
// ])
</script>

<template>
  <main class="text-white">
    <center class="pt-60">
    <!-- Padding bg-blue-500  -->
      <h1 class="text-7xl font-semibold">
        Welcome to 
        <span class="text-orange-500 font-semibold text-7xl">Invoicify</span>
      </h1>

      <div>
        <RouterLink to="/invoicer">
          <Button class="mx-4" title="Invoicer" location="/invoicer"/>
        </RouterLink>

        <RouterLink to="/payload">
          <Button class="mx-4" title="Payload"/>
        </RouterLink>

        <RouterLink>
          <Button class="mx-4" title="Verifier" location="/invoicer"/>
        </RouterLink>
        
      </div>
    </center>
  </main>
</template>

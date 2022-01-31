<template>
  <div class="home">
    <dashboard />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Dashboard from "@/components/Dashboard.vue"; // @ is an alias to /src

export default defineComponent({
  name: "DashboardPage",
  components: {
    Dashboard,
  },
});
</script>

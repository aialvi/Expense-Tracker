<template>
  <div class="home">
    <div class="h-screen bg-white">
      <div class="title3 bg-gray-100 bg-opacity-90 py-10 h-full">
        <div
          class="container mx-auto px-4 mt-8 mb-24 flex justify-center lg:flex-row h-30"
        >
          <h1 class="text-4xl font-bold">Expense Tracker</h1>
        </div>
        <div class="container mx-auto px-4 flex flex-col lg:flex-row h-30">
          <div
            class="justify-center title relative lg:w-2/4 rounded-xl bg-gradient-to-r from-blue-100 to-indigo-100 bg-cover p-24"
          >
            <p class="text-secondary text-2xl font-semibold">
              Manage expenses in a minimal way.
            </p>
            <button
              class="mt-20 bg-white font-semibold px-8 py-2 rounded"
              @click="$router.push('/registration')"
            >
              Sign Up
            </button>
          </div>
          <div
            class="title2 mt-6 lg:mt-0 lg:ml-6 lg:w-2/4 rounded-xl bg-gradient-to-r from-indigo-100 to-blue-100 bg-cover p-24"
          >
            <p class="text-secondary text-2xl font-semibold">
              Already have an account?
            </p>
            <button
              class="mt-20 bg-white font-semibold px-8 py-2 rounded"
              @click="
                {
                  $router.push('/login');
                }
              "
            >
              Sign In
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Home",
  components: {},
});
</script>
<style>
.title3 {
  z-index: 10;
  position: relative;
}

.title3::after {
  content: "";
  position: absolute;
  opacity: 0.2;
  z-index: -999;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}

.text-primary {
  color: #f9b529;
}

.text-primary-lite {
  color: #fac251;
}

.text-secondary {
  color: #294356;
}

.text-secondary-lite {
  color: #d5dee5;
}

.bg-primary {
  background-color: #f9b529;
}

.bg-primary-lite {
  background-color: #fac251;
}

.bg-secondary {
  background-color: #294356;
}

.bg-secondary-lite {
  background-color: #d5dee5;
}
</style>

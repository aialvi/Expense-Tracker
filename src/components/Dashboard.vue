<template>
  <div class="bg-white p-8 rounded-md w-full">
    <div class="flex items-center justify-between pb-6">
      <div>
        <h2 class="text-gray-600 font-semibold">Expense Tracker</h2>
      </div>
      <div class="flex items-center justify-between">
        <div class="flex bg-gray-50 items-center p-2 rounded-md">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5 text-gray-400"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
              clip-rule="evenodd"
            />
          </svg>
          <input
            class="bg-gray-50 outline-none ml-1 block"
            type="text"
            name=""
            id=""
            placeholder="search..."
          />
        </div>
        <div class="lg:ml-40 ml-10 space-x-8">
          <button
            class="bg-indigo-600 px-4 py-2 rounded-md text-white font-semibold tracking-wide cursor-pointer"
          >
            New Report
          </button>
          <button
            class="bg-indigo-600 px-4 py-2 rounded-md text-white font-semibold tracking-wide cursor-pointer"
            @click="isActive = true"
          >
            Create
          </button>
        </div>
      </div>
    </div>
    <div>
      <div class="-mx-4 sm:-mx-8 px-4 sm:px-8 py-4 overflow-x-auto">
        <div class="inline-block min-w-full shadow rounded-lg overflow-hidden">
          <table class="min-w-full leading-normal">
            <thead>
              <tr>
                <th
                  class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-xs font-semibold text-gray-600 uppercase tracking-wider"
                >
                  Date
                </th>
                <th
                  class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-xs font-semibold text-gray-600 uppercase tracking-wider"
                >
                  Reason
                </th>
                <th
                  class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-xs font-semibold text-gray-600 uppercase tracking-wider"
                >
                  Amount
                </th>
                <th
                  class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-xs font-semibold text-gray-600 uppercase tracking-wider"
                >
                  Balance
                </th>
                <th
                  class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-xs font-semibold text-gray-600 uppercase tracking-wider"
                >
                  Type
                </th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td
                  class="px-2 py-5 border-b border-gray-200 bg-white text-center text-sm"
                >
                  <p class="text-gray-900 whitespace-no-wrap">Jan 18, 2020</p>
                </td>
                <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                  <p class="text-gray-900 whitespace-no-wrap">Food</p>
                </td>
                <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                  <p class="text-gray-900 whitespace-no-wrap">219</p>
                </td>
                <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                  <p class="text-gray-900 whitespace-no-wrap">4300</p>
                </td>
                <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                  <span
                    class="relative inline-block px-3 py-1 font-semibold text-green-900 leading-tight"
                  >
                    <span
                      aria-hidden
                      class="absolute inset-0 bg-green-200 opacity-50 rounded-full"
                    ></span>
                    <span class="relative">Credit</span>
                  </span>
                </td>
              </tr>
              <tr>
                <td class="px-2 py-5 bg-white text-sm">
                  <p class="text-gray-900 whitespace-no-wrap">Jan 18, 2020</p>
                </td>
                <td class="px-5 py-5 bg-white text-sm">
                  <p class="text-gray-900 whitespace-no-wrap">Internet Bill</p>
                </td>
                <td class="px-5 py-5 bg-white text-sm">
                  <p class="text-gray-900 whitespace-no-wrap">302</p>
                </td>
                <td class="px-5 py-5 bg-white text-sm">
                  <p class="text-gray-900 whitespace-no-wrap">3022</p>
                </td>
                <td class="px-5 py-5 bg-white text-sm">
                  <span
                    class="relative inline-block px-3 py-1 font-semibold text-red-900 leading-tight"
                  >
                    <span
                      aria-hidden
                      class="absolute inset-0 bg-red-200 opacity-50 rounded-full"
                    ></span>
                    <span class="relative">Debit</span>
                  </span>
                </td>
              </tr>
            </tbody>
          </table>
          <div
            class="px-5 py-5 bg-white border-t flex flex-col xs:flex-row items-center xs:justify-between"
          >
            <span class="text-xs xs:text-sm text-gray-900">
              Showing 1 to 2 of 50 Entries
            </span>
            <div class="inline-flex mt-2 xs:mt-0">
              <button
                class="text-sm text-indigo-50 transition duration-150 hover:bg-indigo-500 bg-indigo-600 font-semibold py-2 px-4 rounded-l"
              >
                Prev
              </button>
              &nbsp; &nbsp;
              <button
                class="text-sm text-indigo-50 transition duration-150 hover:bg-indigo-500 bg-indigo-600 font-semibold py-2 px-4 rounded-r"
              >
                Next
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <create-transaction v-model:isActive="isActive"></create-transaction>
</template>
<script lang="ts">
import CreateTransaction from "./CreateTransaction.vue";
import { defineComponent } from "vue";
export default defineComponent({
  components: {
    CreateTransaction,
  },
  data() {
    return {
      isActive: false,
    };
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
</style>

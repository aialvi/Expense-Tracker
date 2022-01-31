<template>
  <TransitionRoot as="template" v-if="isActive" :show="isActive">
    <Dialog
      as="div"
      class="fixed z-10 inset-0 overflow-y-auto"
      @close="$emit('update:isActive', false)"
    >
      <div
        class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0"
      >
        <TransitionChild
          as="template"
          enter="ease-out duration-300"
          enter-from="opacity-0"
          enter-to="opacity-100"
          leave="ease-in duration-200"
          leave-from="opacity-100"
          leave-to="opacity-0"
        >
          <DialogOverlay
            class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"
          />
        </TransitionChild>

        <!-- This element is to trick the browser into centering the modal contents. -->
        <span
          class="hidden sm:inline-block sm:align-middle sm:h-screen"
          aria-hidden="true"
          >&#8203;</span
        >
        <TransitionChild
          as="template"
          enter="ease-out duration-300"
          enter-from="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
          enter-to="opacity-100 translate-y-0 sm:scale-100"
          leave="ease-in duration-200"
          leave-from="opacity-100 translate-y-0 sm:scale-100"
          leave-to="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
        >
          <div
            class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full"
          >
            <div class="bg-white px-5 pt-5 pb-4 sm:pb-4">
              <div class="sm:flex sm:items-start">
                <div
                  class="w-full mt-3 text-center sm:mt-0 sm:mx-4 sm:text-left"
                >
                  <DialogTitle
                    as="h3"
                    class="text-lg leading-6 font-medium text-gray-900 mb-5"
                  >
                    Add Transaction
                  </DialogTitle>
                  <DialogDescription>
                    <Form @submit="onSubmit">
                      <div class="flex flex-col px-7 py-5 bg-gray-50 sm:w-full">
                        <p class="mb-2 font-semibold text-gray-700">Reason</p>
                        <Field
                          type="text"
                          name="reason"
                          placeholder="e.g. Rent"
                          class="p-5 mb-5 bg-white border border-gray-200 rounded shadow-sm h-12"
                          v-model="form.reason"
                        />
                        <div
                          class="flex flex-col sm:flex-row items-center mb-5 sm:space-x-5"
                        >
                          <div class="w-full mt-2 sm:mt-0">
                            <p class="mb-2 font-semibold text-gray-700">
                              Amount
                            </p>
                            <Field
                              type="number"
                              name="amount"
                              min="0"
                              placeholder="e.g. 100"
                              class="w-full p-5 bg-white border border-gray-200 rounded shadow-sm h-16"
                              v-model="form.amount"
                            />
                          </div>
                        </div>
                        <div
                          class="flex flex-col sm:flex-row items-center mb-5 sm:space-x-5"
                        >
                          <div class="w-full">
                            <p class="mb-2 font-semibold text-gray-700">Type</p>
                            <select
                              name="type"
                              class="w-full p-5 bg-white border border-gray-200 rounded shadow-sm appearance-none"
                              placeholder="Select type..."
                              v-model="form.type"
                            >
                              <option>Debit</option>
                              <option>Credit</option>
                            </select>
                          </div>
                        </div>

                        <div
                          class="flex flex-col sm:flex-row items-center mb-5 sm:space-x-5"
                        >
                          <div class="w-full mt-2 sm:mt-0">
                            <p class="mb-2 font-semibold text-gray-700">Date</p>
                            <Field
                              class="w-full p-5 bg-white border border-gray-200 rounded shadow-sm appearance-none"
                              type="date"
                              name="date"
                              v-model="form.date"
                            />
                          </div>
                        </div>
                      </div>
                    </Form>
                  </DialogDescription>
                </div>
              </div>
            </div>
            <div
              class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse"
            >
              <button
                type="button"
                class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-blue-600 text-base font-medium text-white hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500 sm:ml-3 sm:w-auto sm:text-sm"
                @click="onSubmit"
              >
                Save
              </button>
              <button
                type="button"
                class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm"
                @click="$emit('update:isActive', false)"
                ref="cancelButtonRef"
              >
                Cancel
              </button>
            </div>
          </div>
        </TransitionChild>
      </div>
    </Dialog>
  </TransitionRoot>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import {
  Dialog,
  DialogOverlay,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import { Form, Field } from "vee-validate";

export default defineComponent({
  components: {
    Dialog,
    DialogOverlay,
    DialogTitle,
    TransitionChild,
    TransitionRoot,
    Form,
    Field,
  },
  props: {
    isActive: Boolean,
  },
  methods: {
    onSubmit() {
      console.log(this.form);
      this.$emit("update:isActive", false);
    },
  },
  data() {
    return {
      form: {
        reason: "",
        type: "Debit",
        amount: "",
        date: new Date().toISOString().split("T")[0],
      },
    };
  },
});
</script>

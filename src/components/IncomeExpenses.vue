<template>
  <div class="inc-exp-container">
    <div>
      <h4>GELİR</h4>
      <p id="money-plus" class="money plus">{{ formatCurrency(income) }}</p>
    </div>
    <div>
      <h4>GİDER</h4>
      <p id="money-minus" class="money minus">{{ formatCurrency(expenses) }}</p>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
import { formatCurrency } from "@/utils/utils.js";

const props = defineProps({
  income: {
    type: Number,
    required: true,
  },
  expenses: {
    type: Number,
    required: true,
  },
});
</script>

<template>
  <h3>Yeni İşlem Ekle</h3>
  <form id="form" @submit.prevent="onsubmit">
    <div class="form-control">
      <label for="text">Araç</label>
      <input
        type="text"
        id="text"
        v-model="text"
        placeholder="Aracın ismi yazınız..."
      />
    </div>
    <div class="form-control">
      <label for="amount">Miktar</label>
      <input
        type="number"
        id="amount"
        v-model="amount"
        placeholder="Miktarı giriniz..."
      />
    </div>
    <button class="btn">Ekle</button>
  </form>
</template>

<script setup>
import { ref } from "vue";
import { useToast } from "vue-toastification";

const text = ref("");
const amount = ref("");

const emit = defineEmits(["transactionSubmitted"]);

const toast = useToast();

const onsubmit = () => {
  if (!text.value || !amount.value) {
    toast.error("Araç ve Miktarı yazılmalıdır!");
    return;
  }

  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value),
  };

  emit("transactionSubmitted", transactionData);

  text.value = "";
  amount.value = "";
};
</script>

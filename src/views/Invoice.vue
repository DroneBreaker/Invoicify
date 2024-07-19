<template>
  <div class="h-[100%] text-gray-400">
    <center>
      <div class="w-[35rem] p-2">
        <div class="bg-gray-900 w-[40rem] p-4 rounded-lg">
          <h1 class="text-3xl font-bold mb-2">Issue your Invoice</h1>

          <form action="/">
            <div class="mb-2">
              <!-- <label for="invoiceNumber">Invoice Number:</label> -->
              <input class="w-[80%] rounded-md p-2 px-4 bg-gray-300" type="number" id="totalLevy" placeholder="Total Levy" disabled required />
            </div>

            <div class="mb-2">
              <!-- <label for="invoiceNumber">Invoice Number:</label> -->
              <select class="w-[80%] rounded-md p-2 px-4" name="calculationType" id="calculationType">
                <option value="calculationType">Calculation Type</option>
                <option value="inclusive">Inclusive</option>
                <option value="exclusive">Exclusive</option>
              </select>

              <!-- <input class="w-[80%] rounded-md p-2 px-4" type="text" id="calculationType" placeholder="Calculation Type" required /> -->
            </div>

            <div class="mb-2">
              <!-- <label for="invoiceNumber">Invoice Number:</label> -->
              <input class="w-[80%] rounded-md p-2 px-4 bg-gray-300" type="number" id="totalVAT" placeholder="Total VAT" disabled required />
            </div>

            <div class="mb-2">
              <!-- <label for="date">Date:</label> -->
              <input class="w-[80%] rounded-md p-2 px-4" type="date" id="transactionDate" required />
            </div>

            <div class="mb-2">
              <!-- <label for="clientName">Client Name:</label> -->
              <input class="w-[80%] rounded-md p-2 px-4 bg-gray-300" type="number" id="totalAmount" placeholder="Total Amount" disabled required />
            </div>

            <div class="mb-2">
              <!-- <label for="clientName">Client Name:</label> -->
              <select class="w-[80%] rounded-md p-2 px-4" name="calculationType" id="calculationType">
                <option value="INCLUSIVE">Sale Type</option>
                <option value="normal">Normal</option>
                <option value="export">Export</option>
              </select>

              <!-- <input class="w-[80%] rounded-md p-2 px-4" type="text" id="saleType" placeholder="Sale Type" required /> -->
            </div>

            <div class="mb-2">
              <!-- <label for="clientName">Client Name:</label> -->
              <input class="w-[80%] rounded-md p-2 px-4" type="text" id="discountType" placeholder="Discount Type" required />
            </div>

            <div class="mb-2">
              <!-- <label for="clientEmail">Client Email:</label> -->
              <input class="w-[80%] rounded-md p-2 px-4" type="number" id="discountAmount" placeholder="Discount Amount" required />
            </div>

            <div class="mb-2">
              <!-- <label for="clientEmail">Client Email:</label> -->
              <input class="w-[80%] rounded-md p-2 px-4" type="text" id="reference" placeholder="Reference" required />
            </div>

            <div class="mb-2">
              <!-- <label for="clientEmail">Client Email:</label> -->
              <input class="w-[80%] rounded-md p-2 px-4" type="text" id="groupReferenceId" placeholder="Group Reference" required />
            </div>

            <div class="mb-2">
              <!-- <label for="totalAmount">Total Amount:</label> -->
              <input class="w-[80%] rounded-md p-2 px-4" type="text" id="purchaseOrderReference" placeholder="Purchase Order Number" required />
            </div>

            <RouterLink to="/">
              <Button class="text-white" title="Submit" />
            </RouterLink>
          </form>
        </div>
      </div>
    </center>
  </div>
</template>

<style>

</style>

<script setup>
/**
 * Imports
*/
  import Button from '@/components/Button.vue';
  import { ref, computed } from 'vue';

/**
 * Declarations
*/
  const totalLevy = ref(0.0);
  let INCLUSIVE;
  let EXCLUSIVE;
  // const username = ref('');
  // const {INVOICE, REFUND, 
  //   PARTIAL_REFUND, REFUND_CANCELLATION, 
  //   PURCHASE, PURCHASE_RETURN, 
  //   PURCHASE_RETURN_CANCELLATIONS, 
  //   CREDIT_NOTE, DEBIT_NOTE
  // } = flag;
  const calculationType = ref(
    { INCLUSIVE, EXCLUSIVE}
  );
  let totalVAT;
  // let transactionDate;
  const totalAmount = ref(0.0);
  const voucherAmount = ref(0.0);
  // const businessPartnerName = ref('');
  // const businessTIN = ref('');
  let saleType;
  let discountType;
  const discountAmount = ref(0.0);
  let reference;
  let groupReferenceId;
  let purchaseOrderReference;
  let levyAmountA;
  let levyAmountB;
  let levyAmountC;
  let levyAmountD;
  let levyAmountE;


/**
 * Calculations
*/
  // calculateTotalLevy, totalVAT, totalAmount, voucherAmount, discountAmount
  function calculateTotalLevy() {
    totalLevy.value = levyAmountA + levyAmountB + levyAmountC + levyAmountD + levyAmountE;
  }

  function calculateTotalVAT() {
    totalVAT = totalAmount * 0.15;
  }

  function calculateTotalAmount() {
    totalAmount.value = (totalAmount.value * 1) + voucherAmount.value;
  }

  function calculateVoucherAmount() {
    voucherAmount.value = (totalAmount.value * 0.1) + (totalAmount.value * 0.05);
  }

  function calculateDiscountAmount() {
    discountAmount.value = (totalAmount.value * 0.05);
  }

  // calculate exchange rate
</script>

<template>
  <div class="text-gray-400">
    <center>
      <div class="w-[35rem] p-2 pt-8">
        <div class="bg-gray-900 w-[35rem] p-4 rounded-lg">
          <h1 class="text-3xl font-bold mb-4">Issue your Invoice</h1>

          <form class="justify-between" action="/">
              <div class="mb-4"> 
              <!-- <label for="invoiceNumber">Invoice Number:</label> -->
              <select class="w-[45%] rounded-md p-2 px-4" name="calculationType" id="calculationType">
                <option value="calculationType">Calculation Type</option>
                <option value="inclusive">Inclusive</option>
                <option value="exclusive">Exclusive</option>
              </select>

              <!-- <input class="w-[80%] rounded-md p-2 px-4" type="text" id="calculationType" placeholder="Calculation Type" required /> -->

              <!-- <label for="invoiceNumber">Invoice Number:</label> -->
              <input class="w-[45%] rounded-md p-2 px-4 mx-4 bg-gray-300" type="number" :value="totalLevy" id="totalLevy" placeholder="Total Levy" readonly required />

            </div>

            <div class="mb-4">
              <!-- <label for="invoiceNumber">Invoice Number:</label> -->
              <input class="w-[45%] rounded-md p-2 px-4 bg-gray-300" type="number" :value="totalVAT" placeholder="Total VAT" readonly required />

              <input class="w-[45%] rounded-md p-2 px-4 mx-4" type="date" id="transactionDate" required />
            </div>

            <div class="mb-4">
              <!-- <label for="date">Date:</label> -->

              <!-- <label for="clientName">Client Name:</label> -->
              <input class="w-[45%] rounded-md p-2 px-4 bg-gray-300" type="number" :value="totalAmount" id="totalAmount" placeholder="Total Amount" readonly required />

              <select class="w-[45%] rounded-md p-2 px-4 mx-4" name="calculationType" id="calculationType">
                <option value="INCLUSIVE">Sale Type</option>
                <option value="normal">Normal</option>
                <option value="export">Export</option>
              </select>
            </div>

            <div class="mb-4">
              <select class="w-[45%] rounded-md p-2 px-4" name="discountType" id="discountType">
                <option value="discountType">Discount Type</option>
                <option value="general">General</option>
                <option value="selective">Selective</option>
              </select>

              <input class="w-[45%] rounded-md p-2 px-4 mx-4" type="number" id="discountAmount" placeholder="Discount Amount" required />
            </div>

            <div class="mb-4">
              <input class="w-[45%] rounded-md p-2 px-4" type="text" id="reference" placeholder="Reference" required />
            
              <select class="w-[45%] rounded-md p-2 px-4 mx-4" name="tourismOption" id="tourismOption">
                <option value="tourismOption">Tourism Option</option>
                <option value="yes">Yes</option>
                <option value="no">No</option>
              </select>
            </div>

            <div class="mb-6">
              <!-- <label for="clientEmail">Client Email:</label> -->
              <select class="w-[45%] rounded-md p-2 px-4" name="cstOption" id="cstOption">
                <option value="cstOption">CST Option</option>
                <option value="yes">Yes</option>
                <option value="no">No</option>
              </select>

              <input class="w-[45%] rounded-md p-2 px-4 mx-4" type="text" id="purchaseOrderReference" placeholder="Purchase Order Number" required />
            </div>

            <div class="mb-4">
              <input class="w-[45%] rounded-md p-2 px-4" type="number" v-model="quantity" value="quantity" placeholder="Quantity" required />

              <input class="w-[45%] rounded-md p-2 px-4 mx-4" type="number" v-model="unitPrice" value="unitPrice" placeholder="Unit Price" required />
            </div>

            <div class="mb-4">
              <select class="w-[45%] rounded-md p-2 px-4" name="cstOption" id="cstOption">
                <option value="cstOption">CST Option</option>
                <option value="yes">Yes</option>
                <option value="no">No</option>
              </select>

              <!-- <input class="w-[45%] rounded-md p-2 px-4 mx-4" type="number" v-model="unitPrice" value="unitPrice" placeholder="Unit Price" required /> -->
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
  // const totalLevy = ref(0.0);
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
  // let totalVAT;
  // let transactionDate;
  let totalAmount = ref('');
  const unitPrice = ref('');
  const quantity = ref('');
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
  // function calculateTotalLevy() {
  //   document.getElementById("totalLevy").value = totalLevy;
  //   totalLevy.value = levyAmountA + levyAmountB + levyAmountC + levyAmountD + levyAmountE;

  //   return totalLevy;
  // }


  function calculateTotalVAT() {
    document.getElementById("totalVAT").value = totalVAT;
    totalVAT = totalAmount * 0.15;

    return totalVAT;
  }


  // function calculateTotalAmount() {
  //   totalAmount.value = quantity.value * unitPrice.value;
  // }

  function calculateVoucherAmount() {
    voucherAmount.value = (totalAmount.value * 0.1) + (totalAmount.value * 0.05);
  }

  function calculateDiscountAmount() {
    discountAmount.value = (totalAmount.value * 0.05);
  }

/**
 * Computed calculations
*/
  // calculation of the total amount
  // const totalAmount = computed(() => {
  //   document.getElementById("totalAmount");
  //   const totalAmount = unitPrice * quantity;

  //   return {
  //     totalAmount
  //   }
  // });

  totalAmount = computed(() => quantity.value * unitPrice.value);

  // calculation of the levies

  
  const totalVAT = computed(() => totalAmount.value * 0.15);
  // const totalLevy = computed(() => {
  //   const totalLevy = levyAmountA + levyAmountB + levyAmountC + levyAmountD + levyAmountE;

  //   return {
  //     totalLevy
  //   }
  // })

  // const totalVAT = computed(() =>{
  //   document.getElementById("totalVAT").value = totalVAT;
  //   const totalVAT = totalAmount * 0.15;

  //   return {
  //     totalVAT
  //   }
  // })



  // calculate exchange rate
</script>

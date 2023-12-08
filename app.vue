<script setup lang="ts">
import { loadScript } from '@paypal/paypal-js';
let paypal;
try {
  paypal = await loadScript({ clientId: process.env.PAYPAL_CLIENT_ID as string });
} catch (error) {
  console.error(error);
}
if (paypal) {
  try {
    await paypal.Buttons().render('#paypal-buttons');
  } catch (error) {
    console.error('failed to load buttons', error);
  }
}
</script>
<template>
  <div class="flex justify-center items-center h-[100]" >
    <div id="paypal-buttons"></div>
  </div>
</template>

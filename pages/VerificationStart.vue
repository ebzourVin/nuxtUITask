
<template>
  <UContainer class="flex items-center justify-center">
    <UCard class="rounded-lg shadow-lg max-w-md ">

        <h2 class="text-xl font-bold py-2">Verification</h2>
        <div class="my-3">
            <p class="py-1">How Would You Prefer to Proceed?</p>
        </div>


        <div class=" flex flex-col items-center space-y-4">
        
         <UButton
          @click="handlePhoneOption"
          icon="i-heroicons-device-phone-mobile" 
          color="gray" 
          size="xl"
          variant="ghost" 
          class="w-full h-auto border border-gray-200 dark:border-gray-700 " 
          :ui="{ rounded: 'rounded-lg', padding: { sm: 'p-3' } }">
            <div class="flex flex-col items-start mr-8">
                <p>
                    +1 XXX-XXX-1050
                </p>
                <p class="text-sm text-gray-600">
                    Messaging and data rates may apply.
                </p>
            </div>
            <template #trailing>
                <UIcon
                    name="i-heroicons-chevron-right"
                />
            </template>
        </UButton>

        <UButton 
        @click="handleEmailOption"
         icon="i-heroicons-envelope" 
         size="xl"
         color="gray" 
         variant="ghost" 
         class="w-full h-auto border border-gray-200 dark:border-gray-700"
          :ui="{ rounded: 'rounded-lg', padding: { sm: 'p-3' } }">
            <p class="mr-32">
                user@example.com
            </p> 
            <template #trailing>
                <UIcon
                    name="i-heroicons-chevron-right"
                    class="float-right"
                />
            </template>
        </UButton>
    </div>
    <div class="mt-20 text-sm">A message containing the verification code will be sent to the option you select.</div>
    </UCard>
  </UContainer>
</template>
    
<script setup>

const handlePhoneOption=()=>{
    navigateTo(`verification/phone`);

}

 const handleEmailOption=()=>{
    navigateTo(`verification/email`);

 }

</script>

<style>

</style>
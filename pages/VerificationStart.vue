<template>
  <UCard class="flex flex-col rounded-lg shadow-lg w-full h-full space-y-2.5 justify-between" :ui="{body:{padding:'px-14 py-14 sm:p-14'}}" >

        <div class="flex flex-row">
            <div class="flex-col">
                <h2 class="text-4xl font-bold my-3">Verification</h2>
            </div>
        </div>


        <div class="flex flex-row my-8">

            <div class="flex flex-col w-full space-y-2.5">  

                <div class="flex flex-row ">
                    <p class="py-1">How Would You Prefer to Proceed?</p>
                </div>

                <UButton
                @click="handlePhoneOption"
                icon="" 
                color="gray" 
                size="xl"
                variant="ghost" 
                class="flex flex-row justify-between w-full h-auto border gap-2 border-gray-200 dark:border-gray-700 " 
                :ui="{ rounded: 'rounded-lg', padding: { xl: 'py-8 pr-10 pl-5' },icon:{size:{xl:'h-8 w-8'}} }">
                    <div class="flex flex-col items-start">
                        <div class="flex flex-row gap-4">
                            <div class="flex flex-col justify-center">
                                <UIcon
                                    name="i-heroicons-device-phone-mobile w-10 h-10"
                                />
                            </div>
                            <div class="flex flex-col items-start">
                                <p>
                                    +1 XXX-XXX-1050
                                </p>
                                <p class="text-sm text-gray-600">
                                    Messaging and data rates may apply.
                                </p>
                            </div>
                        </div>

                    </div>
                    <template #trailing>
                        <UIcon
                            name="i-heroicons-chevron-right"
                        />
                    </template>
                </UButton>

                <UButton 
                @click="handleEmailOption"
                icon="" 
                size="xl"
                color="gray" 
                variant="ghost" 
                class="flex flex-row justify-between w-full h-auto border border-gray-200 dark:border-gray-700 p-"
                :ui="{ rounded: 'rounded-lg', padding: { xl: 'py-8 pr-10 pl-5' } }">

                    <div class="flex flex-col items-start">
                        <div class="flex flex-row gap-4 items-center">
                            <div class="flex flex-col">
                                <UIcon
                                    name="i-heroicons-envelope w-10 h-10"
                                />
                            </div>
                            <div class="flex flex-col items-start">
                                <p>
                                    user@example.com
                                </p>
                            </div>
                        </div>

                    </div>
                    <template #trailing>
                        <UIcon
                            name="i-heroicons-chevron-right"
                            class=""
                        />
                    </template>
                </UButton>
                <div class="flex flex-row">
            <div class="flex flex-col">
                <div class="text-[#D8D8D5] text-base">A message containing the verification code will be sent to the option you select.</div>
            </div>
        </div>
            </div>
            
        </div>


    </UCard>
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
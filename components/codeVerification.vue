
<template>
    <UContainer class="flex items-center justify-center">
      <UCard class="rounded-lg shadow-lg max-w-md  w-[500px] h-[400px] px-5 ">
  
          <h2 class="text-xl font-bold py-2">Verification</h2>
          
          <slot name="verficationPageHeader"></slot>
  
          <div class=" flex flex-col items-center justify-center space-y-4">

            <UForm class="space-y-4 flex  items-baseline gap-3" @submit="">
                <UInput type="text" maxlength="1" />
                <UInput type="text" maxlength="1" />
                <UInput type="text" maxlength="1" />
                <UInput type="text" maxlength="1" />
                <UInput type="text" maxlength="1" />
                <UInput type="text" maxlength="1" />
            </UForm>
            <UButton  block color="orange" size="xl" type="submit" @click="handleBtnClick" >Cotinue</UButton>
        </div>
      </UCard>
    </UContainer>
  </template>
      
  <script setup>
   const handleBtnClick=()=>{
  }
  
  </script>
  
  <style scoped>

  </style>
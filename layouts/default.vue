<template>

    <UCard class="flex flex-col h-screen items-center justify-center">
      <div class=" flex flex-row py-4 px-9" >
       <PageHeader/>
      </div>
      <!-- Page Content -->
      <UContainer class="w-[600px] h-[650px] px-5 ">
        <slot/>
      </UContainer>
      <div class=" flex flex-col items-center py-4" >
       <PageFooter/>
      </div>
    </UCard>
</template>

<script setup>
import PageFooter from '~/components/PageFooter.vue';
import PageHeader from '~/components/PageHeader.vue';
</script>

<style>

</style>
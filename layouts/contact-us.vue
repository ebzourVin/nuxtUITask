<template>
    <UCard class="flex flex-col h-screen items-center justify-center">
      <div class=" flex flex-row py-4" >
       <PageHeader/>
      </div>
      <!-- Page Content -->
      <UContainer class="flex flex-row w-[600px] h-[650px] px-5 ">
        <slot/>
      </UContainer>
    </UCard>
</template>

<script setup>
import PageHeader from '~/components/PageHeader.vue';
</script>

<style>

</style>
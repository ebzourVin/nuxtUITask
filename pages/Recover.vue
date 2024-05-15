<template>
    <UCard class="flex flex-col content-center w-full h-full" :ui="{body:{padding:'px-14 py-14 sm:p-14'}}">

      <div class="flex flex-row">
          <div class="flex flex-col space-y-8">

            <div class="flex flex-row">
              <h2 class="text-4xl font-bold my-3">Recover</h2>
            </div>


            <div class="flex flex-row items-center justify-center">
              <svg width="105.2" height="106.99" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M3 8L10.89 13.26C11.2187 13.4793 11.6049 13.5963 12 13.5963C12.3951 13.5963 12.7813 13.4793 13.11 13.26L21 8M5 19H19C19.5304 19 20.0391 18.7893 20.4142 18.4142C20.7893 18.0391 21 17.5304 21 17V7C21 6.46957 20.7893 5.96086 20.4142 5.58579C20.0391 5.21071 19.5304 5 19 5H5C4.46957 5 3.96086 5.21071 3.58579 5.58579C3.21071 5.96086 3 6.46957 3 7V17C3 17.5304 3.21071 18.0391 3.58579 18.4142C3.96086 18.7893 4.46957 19 5 19Z" stroke="black" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
            </div>

            <div class="flex flex-row">
              <p>Enter the sign-in ID for your account. We'll send a link to recover your account.</p>
            </div>
              
          </div>
      </div>

      <div class="flex flex-row">
        <div class="flex-col w-full">
          <UForm id="recoveryForm" :state="formState" :schema="recoverSchema" class="space-y-4" @submit="onSubmit">
            <UFormGroup name="email" label="" class="mt-4" required>
              <UInput size="xl" 
              placeholder="michelle.rivera@example.com"
              icon="i-heroicons-envelope" 
              v-model="formState.email" 
              variant="none"
              class="border-b border-gray-200 dark:border-gray-700" />
            </UFormGroup>

            <UButton  block color="orange" size="xl" type="submit" :disabled="!formState.email || !recoverSchema.safeParse(formState).success">Cotinue</UButton>
          </UForm>
        </div>   
      </div>
    </UCard>
  </template>
  
  <script setup lang="ts">
  
  import { z } from 'zod'
  import type { FormSubmitEvent } from '#ui/types'
  import {recoverSchema} from '~/schemas/RecoverFormSchema'

  type RecoverSchema = z.output<typeof recoverSchema>

  const formState= ref({
    email:'',
  });

  async function onSubmit (event: FormSubmitEvent<RecoverSchema>) {
    // Do something with data
    console.log(event.data)
  }
  </script>
  
  
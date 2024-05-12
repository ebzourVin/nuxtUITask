<template>
    <UContainer class="flex flex-col content-center">
        <UCard class="w-[500px]">
            <template #header>
              <h2 class="text-xl font-bold">Recover</h2>
            </template>
            <UForm id="recoveryForm" :state="formState" :schema="recoverSchema" class="space-y-4" @submit="onSubmit">
              <span class="flex flex-col items-center justify-center"><i class="i-heroicons-envelope text-8xl"></i>
                Enter the sign-in ID for your account. We'll send a link to recover your account.
            </span>

              <UFormGroup name="email" label="Email" class="mt-4" required>
                <UInput size="xl" placeholder="Email" icon="i-heroicons-envelope" v-model="formState.email" />
              </UFormGroup>

              <UButton  block color="orange" size="xl" type="submit" :disabled="!formState.email || !recoverSchema.safeParse(formState).success">Cotinue</UButton>
            </UForm>
        </UCard>
    </UContainer>
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
  
  
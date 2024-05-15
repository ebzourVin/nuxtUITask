<template>
  <UCard class="flex flex-col content-center w-full h-full " :ui="{body:{padding:'px-14 py-14 sm:p-14'}}">

    <div class="flex flex-row">
      <div class="flex-col">
          <h2 class="text-4xl font-bold">Sign in</h2>
      </div>
    </div>

    <div class="flex flex-row ">
        <UForm :state="formState" :schema="signInSchema" class="flex flex-col w-full" @submit="onSubmit">
          <div class="flex-row">
            <div class="flex flex-col my-14">
              <UFormGroup name="email" label="Email Address" class="">
              <UInput
                placeholder="michelle.rivera@example.com"
                icon="i-heroicons-envelope"
                v-model="formState.email"
                variant="none"
                size="xl"
                class="border-b border-gray-200 dark:border-gray-700" 
                :ui="{
                  icon:{
                    size:{
                      xl:'h-5 w-5'
                    }
                  }
                }"
                />
              </UFormGroup>

              <UFormGroup name="password" label="Password" class="mt-8" >
              <UInput
                type="password"
                placeholder="Password"
                icon="i-heroicons-lock-closed"
                v-model="formState.password"
                variant="none"
                size="xl"
                :ui="{
                  icon:{
                    size:{
                      xl:'h-5 w-5'
                    }
                  }
                }"
                class="border-b border-gray-200 dark:border-gray-700"
                />
              <span >
                <NuxtLink to="/Recover" class="text-[#EE7203] float-right text-sm mt-4">Forgot Password?</NuxtLink>
              </span>
              </UFormGroup>
              </div>
          </div>
          
          <div class="flex-row">
            <UButton  block color="orange" size="xl" type="submit" :disabled="!formState.email || !signInSchema.safeParse(formState).success">Cotinue</UButton>
          </div>

        </UForm>
    </div>

          
  </UCard>
</template>

<script setup lang="ts">


import { z } from 'zod'
import type { FormSubmitEvent } from '#ui/types'
import {signInSchema} from '~/schemas/SignInFormSchema'
import axios from 'axios';
import { useRouter } from 'vue-router'; // Import the router
import type { variants } from '#tailwind-config';

type SignInSchema = z.output<typeof signInSchema>

const formState= ref({
  email:'',
  password:'',
});

async function onSubmit (event: FormSubmitEvent<SignInSchema>) {
    try {
    // Send form data to the server for validation
    const response = await axios.post('/api/auth/signin', {
      email: event.data.email,
      password: event.data.password,
    });

    // Handle the response from the server
    if (response.data.token) {
      // Successful authentication
      // Save the token (e.g., in local storage or Vuex store)
      // Redirect the user to the dashboard or another route
      const router = useRouter();
      router.push('/VerificationStart');
      
      console.log('Authentication successful! Token:', response.data.token);
    } else {
      // Invalid credentials
      console.error('Invalid email or password.');
    }
  } catch (error) {
    // Handle any network errors or server issues
    console.error('An error occurred during authentication:', error);
  }
    console.log(event.data)
}
</script>


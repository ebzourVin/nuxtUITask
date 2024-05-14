<template>


  <UContainer class="flex flex-col content-center ">
      <UCard >

          <div>
            <h2 class="text-xl font-bold">Sign in</h2>
          </div>

          <UForm :state="formState" :schema="signInSchema" class="space-y-4" @submit="onSubmit">
          
            <div class="my-14">
                <UFormGroup name="email" label="Email Address" class="mt-4">
                <UInput
                  placeholder="michelle.rivera@example.com"
                  icon="i-heroicons-envelope"
                  v-model="formState.email"
                  variant="none"
                  class="border-b border-gray-200 dark:border-gray-700" 
                  />
              </UFormGroup>

              <UFormGroup name="password" label="Password" class="mt-4" >
                <UInput
                  type="password"
                  placeholder="Password"
                  icon="i-heroicons-lock-closed"
                  v-model="formState.password"
                  variant="none"
                  class="border-b border-gray-200 dark:border-gray-700"
                  />
                <span >
                  <NuxtLink to="/Recover" class="text-[#EE7203] float-right">Forgot Password?</NuxtLink>
                </span>
              </UFormGroup>
            </div>

            <UButton  block color="orange" size="xl" type="submit" :disabled="!formState.email || !signInSchema.safeParse(formState).success">Cotinue</UButton>

          </UForm>
      </UCard>
  </UContainer>
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


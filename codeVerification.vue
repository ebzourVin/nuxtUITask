
<template>
    <UCard class="flex flex-col content-center w-full h-full" :ui="{body:{padding:'px-14 py-14 sm:p-14'}}">
  
      <div class="flex flex-row">
        <div class="flex flex-col w-full">
          <h2 class="text-4xl font-bold py-2">Verification</h2>

        </div>
      </div>

      <div class="flex flex-row">
        <div class="flex flex-col w-full">
          <slot name="verficationPageHeader">
            
          </slot>
        </div>
      </div>

      
      <div class="flex flex-row">
        <div class=" flex flex-col items-center justify-center space-y-4">
          <UForm :state="state" :schema="schema" class=" flex flex-row items-baseline gap-3" @submit="handleBtnClick" @error="onError">
            <div class="flex-col">
              <div class="flex flex-row space-x-2">
                <UFormGroup v-for="(input, index) in state.numbers" :eager-validation="true" :key="index" :id="`input-${index}`" name="state.numbers" class="">
                    <UInput  
                      ref="inputRefs"
                      type="text"
                      :id="`validate-input-${index}`"
                      maxlength="1"
                      v-model="state.numbers[index]"
                    />
                </UFormGroup>
              </div>

              <div class=" w-full flex flex-row items-center justify-center my-12">
                <CountdownTimer @timer-finished="showRequestAgain=true" />
                <p v-show="showRequestAgain">Request Again?
                  <NuxtLink @click="handleResendClick" class="text-[#EE7203] cursor-pointer">Resend  </NuxtLink>
                  <span class="text-gray-500"> | </span>
                  <NuxtLink v-if="pageType==='email'" to="/verification/phone" class="text-[#EE7203]">Get Via SMS</NuxtLink>
                  <NuxtLink v-else-if="pageType==='phone'" to="/verification/email" class="text-[#EE7203]">Get Via email</NuxtLink>
                </p>
              </div>

                <div class="w-full flex flex-row">
                  <UButton  block color="orange" size="xl" type="submit" :disabled="!schema.safeParse(state).success" >Cotinue</UButton>
                </div>
            </div>
 
          </UForm>
        </div>
      </div>
    </UCard>
  </template>
      
  <script setup lang="ts">
    import { z } from 'zod';
    import type { FormError, FormErrorEvent, FormSubmitEvent } from '#ui/types'

   import CountdownTimer from '~/components/CountdownTimer.vue';
   const showRequestAgain = ref(false);

   const props = defineProps(['pageType']);
   const pageType = props.pageType;

  const state = reactive({
    numbers: [null, null, null, null, null, null]
  })

  const inputRefs = ref([])

  const schema = z.object({
      numbers: z.array(z.string()).refine(inputs => inputs.filter(value => value != null).length == 6)
  })


    async function onSubmit () {
  // Do something with data
  console.log({ numbers: state.numbers })
}
  function handleBtnClick(){
    console.log({
      value: schema.safeParse(state)
    })
  }


  async function onError (event: FormErrorEvent) {
    console.log({ event })
    const element = document.getElementById(event.errors[0].id)
    element?.focus()
    element?.scrollIntoView({ behavior: 'smooth', block: 'center' })
  }

  function handleResendClick(){
  }

  onMounted(()=>{
    inputRefs.value.forEach((input,index)=>{
      input.input.addEventListener('input',(event)=>{ 
          if(event.inputType==='deleteContentBackward'){

            if(event.target.value.trim()===''){
            const prevIndex = (index-1)%inputRefs.value.length;
            inputRefs.value[prevIndex].input.focus();
            }
          } else if(event.value.trim() !==''){
            const nextIndex = (index+1)%inputRefs.value.length;
            inputRefs.value[nextIndex].input.focus();
          }
        });
      })
    })
  </script>
  
  <style scoped>
    
  </style>
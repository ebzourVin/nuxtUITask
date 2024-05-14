
<template>
    <UContainer class="flex items-center justify-center">
      <UCard class="rounded-lg shadow-lg max-w-md ">
  
          <h2 class="text-xl font-bold py-2">Verification</h2>
          
          <slot name="verficationPageHeader">
            
          </slot>
  
          <div class=" flex flex-col items-center justify-center space-y-4">

            <pre>{{ state?.numbers }}</pre>
            <br>
            <pre>{{ schema.safeParse(state) }}</pre>

            <UForm :state="state" :schema="schema" class="space-y-4 flex  items-baseline gap-3" @submit="handleBtnClick" @error="onError">
              <UFormGroup class="flex flex-col" v-for="(input, index) in state.numbers" :eager-validation="true" :key="index" :id="`input-${index}`" name="state.numbers">
                <UInput
                  type="text"
                  :id="`validate-input-${index}`"
                  maxlength="1"
                  v-model="state.numbers[indexs]"
                />
              </UFormGroup>

            <UButton  block color="orange" size="xl" type="submit"  >Cotinue</UButton>

       
                <!-- <UInput ref="input2" type="text" maxlength="1" />
                <UInput ref="input3" type="text" maxlength="1" />
                <UInput ref="input4" type="text" maxlength="1" />
                <UInput ref="input5" type="text" maxlength="1"/>
                <UInput ref="input6" type="text" maxlength="1" /> -->
            </UForm>
            <div class="my-12">
              <CountdownTimer @timer-finished="showRequestAgain=true" />
              <p v-show="showRequestAgain">Request Again?
                <NuxtLink @click="handleResendClick" class="text-[#EE7203]">Resend | </NuxtLink>
                <NuxtLink v-if="pageType==='email'" to="/verification/phone" class="text-[#EE7203]">Get Via SMS</NuxtLink>
                <NuxtLink v-else-if="pageType==='phone'" to="/verification/email" class="text-[#EE7203]">Get Via email</NuxtLink>
              </p>
            </div>

        </div>
      </UCard>
    </UContainer>
  </template>
      
  <script setup lang="ts">
    // import { ref} from 'vue';
    import { z } from 'zod';
    // import type { FormSubmitEvent } from '#ui/types';
    import type { FormError, FormErrorEvent, FormSubmitEvent } from '#ui/types'

   import CountdownTimer from '~/components/CountdownTimer.vue';
   const showRequestAgain = ref(false);

  //  const props = defineProps(['pageType']);

  //  const input1= ref(null);
  //  const input2= ref(null);
  //  const input3= ref(null);
  //  const input4= ref(null);
  //  const input5= ref(null);
  //  const input6= ref(null);

  const state = reactive({
    numbers: [null, null, null, null, null, null]
  })

  const schema = z.object({
    state: z.object({
      numbers: z.array(z.string()).refine(inputs => inputs.filter(value => value != null))
    })
  })

  //  const schema = z.object({
  //   inputRefs:{input1:z.string().min(1,'Please enter a valid code'),}
  //  }).refine((data) => {
  //   console.log(data),
  //   data.inputRefs

  //  }, {
         
  //   });

  //  type Schema = z.output<typeof schema>

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

  const handleResendClick=()=>{
  }
  // onMounted(()=>{
  //   inputRefs.value.forEach((input, index)=>{
  //     console.log(input);

  //     input.value.input.addEventListener('input',(event)=>{
  //       console.log(event);
  //       console.log(event.inputType);
  //       console.log(event.target);

  //       if(event.inputType==='deleteContentBackward'){

  //         if(event.target.value.trim()===''){
  //          const prevIndex = (index-1)%inputRefs.value.length;
  //           inputRefs.value[prevIndex].value.input.focus();
  //         }
  //       } else if(event.value !==''){
  //         const nextIndex = (index+1)%inputRefs.value.length;
  //         inputRefs.value[nextIndex].value.input.focus();
  //       }
  //     });

  //    });
  // })
  </script>
  
  <style scoped>
    
  </style>
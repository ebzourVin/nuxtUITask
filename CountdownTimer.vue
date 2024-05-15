<template>
    <div class="text-center">
      <p v-if="timeInSeconds > 0" class="text-[#EE7203]">{{ minutes }}:{{ seconds }}</p>
    </div>
  </template>
  
  <script setup>
  import { ref} from 'vue';

  const emit = defineEmits(['timer-finished']);
  
  const timeInSeconds = ref(10);

  const minutes = ref(Math.floor(timeInSeconds.value / 60));
  const seconds = ref(timeInSeconds.value % 60);
  
  const updateTimer = () => {
    timeInSeconds.value--;
    minutes.value = Math.floor(timeInSeconds.value / 60);
    seconds.value = timeInSeconds.value % 60;


    if (timeInSeconds.value === 0) {
      emit('timer-finished');
      clearInterval(timerInterval);
    }
  };
  // const timerInterval = setInterval(updateTimer, 1000); 

  onMounted(()=>{
  });
  // onNuxtReady(()=>{
  //   const timerInterval = setInterval(updateTimer, 1000); ;
  // })
  onBeforeMount(()=>{
    const timerInterval =  setInterval(updateTimer, 1000);
  });
  
  // onUnmounted(() => {
  //   clearInterval(timerInterval);
  // });
  
  </script>
  
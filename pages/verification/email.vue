
<template>
    <codeVerification>
         <template v-slot:links>
             <a href="#"> sign up now </a>
             <a href="#"> more </a>
           </template>
           <h1>{{header}}</h1>
           <p> {{text}}</p>
       </codeVerification>
     </template>
         
     <script setup>
    import codeVerification from '~/components/codeVerification.vue';
   
   
      const handleBtnClick=()=>{
     }
     
     </script>
     
     <style >
   
     </style>
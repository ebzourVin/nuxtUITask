
<template>
<UContainer class="flex flex-col content-center">
        <UCard class="">

              <h2 class="text-xl font-bold py-2">Support</h2>
              <div class="my-3">
                <p class="py-1">How can we help you?</p>
                <UButton color="white" icon="i-heroicons-envelope" size="xl" type="submit" class="w-full py-8 px-4" @click="" >Email Us</UButton>
              </div>
              
              <div class="my-3">
                <p class="py-1">Frequently Asked questions</p>
                <UAccordion :items="FAQItems" :ui="{ wrapper: 'flex flex-col w-full border border-gray-200 dark:border-gray-700 rounded-lg' }">
                    <template #default="{ item, open }">
                        <UButton color="gray" variant="ghost" class="border-b border-t border-gray-200 dark:border-gray-700" :ui="{ rounded: 'rounded-sm', padding: { sm: 'p-3' } }">
                            <span class="truncate">{{ item.label }}</span>
                            <template #trailing>
                            <UIcon
                                name="i-heroicons-chevron-down-20-solid"
                                class="w-5 h-5 ms-auto transform transition-transform duration-200"
                                :class="[open && 'rotate-180']"
                            />
                            </template>
                        </UButton>
                    </template>
                </UAccordion>
              </div>
        </UCard>
    </UContainer>
</template>

<script setup>
    definePageMeta({
        layout: "contact-us",
    })
    const FAQItems = [{
    label: 'How do I create an account?',
    defaultOpen: true,
    content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed neque elit, tristique placerat feugiat ac, facilisis vitae arcu. Proin eget egestas augue. Praesent ut sem nec arcu pellentesque aliquet. Duis dapibus diam vel metus tempus vulputate.'
    }, {
    label: 'How can I change my email address or phone number?',
    content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed neque elit, tristique placerat feugiat ac, facilisis vitae arcu. Proin eget egestas augue. Praesent ut sem nec arcu pellentesque aliquet. Duis dapibus diam vel metus tempus vulputate.'
    }, {
    label: 'How do I report a problem or bug?',
    content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed neque elit, tristique placerat feugiat ac, facilisis vitae arcu. Proin eget egestas augue. Praesent ut sem nec arcu pellentesque aliquet. Duis dapibus diam vel metus tempus vulputate.'
    }, {
    label: 'Can I use your service on multiple devices?',
    content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed neque elit, tristique placerat feugiat ac, facilisis vitae arcu. Proin eget egestas augue. Praesent ut sem nec arcu pellentesque aliquet. Duis dapibus diam vel metus tempus vulputate.'
    },]

</script>

<style>
[id^="headlessui-disclosure-panel"] {
  padding: 10px;
}
</style>
<template>
  <div class="bg-white dark:bg-gray-700 w-full h-44 shadow flex flex-col lg:flex-row justify-between items-center py-4 px-0 sm:px-52 mt-12">
    <div class="flex flex-col mb-5 xl:mb-0">
        <div><h4 class="text-base mb-2 dark:text-gray-300">{{$t('ContactMe')}}:</h4></div>
        <hr class="mb-2">
        <div class="flex space-x-1 mb-1 text-gray-500 dark:text-gray-300 xl:tracking-tight text-sm lg:text-base">
            <h6 class="font-semibold">{{$t('Phone')}}: </h6><a class="hover:text-turquoise" href="tel:+918110078355">+918110078355</a>
        </div>
        <div class="flex space-x-1 text-gray-500 dark:text-gray-300 xl:tracking-tight text-sm lg:text-base">
            <h6 class="font-semibold">{{$t('Email')}}: </h6><a class="hover:text-turquoise" href="sneshraj.dev@gmail.com">sneshraj.dev@gmail.com</a>
        </div>
    </div>
    <div>
        <v-links/>
    </div>
  </div>
</template>


<script>
import VLinks from "./links.vue"

export default {
    name: 'VFooter',
    components:{VLinks}
}
</script>
<script setup lang="ts">
import { Head, Link } from '@inertiajs/vue3';
import { dashboard, login, register } from '@/routes';

withDefaults(
   defineProps<{
       canRegister: boolean;
   }>(),
   {
       canRegister: true,
   },
);
</script>

<template>
   <Head title="Welcome">
       <link rel="preconnect" href="https://rsms.me/" />
       <link rel="stylesheet" href="https://rsms.me/inter/inter.css" />
   </Head>

   
         <main>

               <Link
                   v-if="$page.props.auth.user"
                   :href="dashboard()"
                   class="inline-block rounded-sm border border-[#19140035] px-5 py-1.5 text-sm leading-normal text-[#1b1b18] hover:border-[#1915014a] dark:border-[#3E3E3A] dark:text-[#EDEDEC] dark:hover:border-[#62605b]"
               >
                   Dashboard
               </Link>
               <template v-else>
                   <Link
                       :href="login()"
                       class="inline-block rounded-sm border border-transparent px-5 py-1.5 text-sm leading-normal text-[#1b1b18] hover:border-[#19140035] dark:text-[#EDEDEC] dark:hover:border-[#3E3E3A]"
                   >
                       Log in
                   </Link>
                   <Link
                       v-if="canRegister"
                       :href="register()"
                       class="inline-block rounded-sm border border-[#19140035] px-5 py-1.5 text-sm leading-normal text-[#1b1b18] hover:border-[#1915014a] dark:border-[#3E3E3A] dark:text-[#EDEDEC] dark:hover:border-[#62605b]"
                   >
                       Register
                   </Link>
               </template>
         </main>
</template>


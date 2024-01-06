<script setup lang="ts">
import VueCountdown from "@chenfengyuan/vue-countdown";

const now = new Date();
const newYear = new Date(now.getFullYear() + 1, 0, 1);
const anni = new Date('2024-06-28');
</script>

<template>
  <div class="space-y-5" v-aos="['animate__slideInUp']" >
    <h1 class="text-4xl font-semibold tracking-tight text-gray-900 dark:text-white sm:text-3xl hover:animate-bounce">
      Chapter IV: Future
      <UIcon name="i-fluent-rocket-20-regular" class="ml-2"/>
    </h1>

    <div class="px-5 py-3 bg-white/20 dark:bg-gray-900/20 backdrop-blur-sm rounded-3xl shadow-lg border border-gray-300 dark:border-gray-600 hover:scale-105 transition duration-500">
      i'm not the best man you've ever met, but i'll always do my best to keep you happy, i want to show you what real
      love looks like and i want to give you the love i never got. No matter what happens i will always be with you
      and do my best because you deserve the world.
    </div>

    <div class="">
      <div class="bg-primary-700 rounded-3xl shadow-lg hover:scale-105 transition duration-500">
        <div class="mx-auto max-w-7xl py-12 px-6 sm:py-16 lg:px-8 lg:py-20">
          <div class="mx-auto max-w-4xl text-center">
            <h2 class="text-3xl font-bold tracking-tight text-white sm:text-4xl">
              Trusted by developers from over 80 planets
            </h2>
            <p class="mt-3 text-xl text-indigo-200 sm:mt-4">
              Lorem ipsum dolor, sit amet consectetur adipisicing
              elit. Repellendus repellat laudantium.
            </p>
          </div>
          <ClientOnly>
            <!--            28 6 2023-->
            <VueCountdown :time="anni - now" v-slot="{ days, hours, minutes, seconds }">
              <dl class="mt-10 text-center sm:mx-auto sm:grid sm:max-w-3xl sm:grid-cols-4 sm:gap-8">
                <div class="flex flex-col">
                  <dt class="order-2 mt-2 text-lg font-medium leading-6 text-primary-200">Hari</dt>
                  <dd class="order-1 text-5xl font-bold tracking-tight text-white">{{ days }}</dd>
                </div>
                <div class="mt-10 flex flex-col sm:mt-0">
                  <dt class="order-2 mt-2 text-lg font-medium leading-6 text-primary-200">Jam</dt>
                  <dd class="order-1 text-5xl font-bold tracking-tight text-white">{{ hours }}</dd>
                </div>
                <div class="mt-10 flex flex-col sm:mt-0">
                  <dt class="order-2 mt-2 text-lg font-medium leading-6 text-primary-200">Menit</dt>
                  <dd class="order-1 text-5xl font-bold tracking-tight text-white">{{ minutes }}</dd>
                </div>
                <div class="mt-10 flex flex-col sm:mt-0">
                  <dt class="order-2 mt-2 text-lg font-medium leading-6 text-primary-200">Menit</dt>
                  <dd class="order-1 text-5xl font-bold tracking-tight text-white">{{ seconds }}</dd>
                </div>
              </dl>
            </VueCountdown>

          </ClientOnly>
        </div>
      </div>
    </div>

  </div>

</template>
<script setup lang="ts">
import type { Container } from 'tsparticles-engine'

// See tsParticles documentation for all available options
const options = {
  background: {
    // color: {
    //   value: '#0d47a1'
    // }
  },
  fullScreen: {
    enable: true,
    zIndex: -1
  },
  fpsLimit: 60,
  interactivity: {
    events: {
      // onClick: {
      //   enable: true,
      //   mode: 'push'
      // },
      onHover: {
        enable: true,
        mode: 'repulse'
      },
    },
    modes: {
      bubble: {
        distance: 400,
        duration: 2,
        opacity: 0.8,
        size: 40
      },
      push: {
        quantity: 4
      },
      repulse: {
        distance: 200,
        duration: 0.4
      }
    }
  },
  particles: {
    color: {
      // value: ['#9333ea', '#dc2626', '#facc15']
      value: ['#9333ea']
    },
    links: {
      // color: ['#9333ea', '#dc2626', '#facc15'],
      color: ['#9333ea'],
      distance: 150,
      enable: true,
      opacity: 0.5,
      width: 1
    },
    move: {
      direction: 'none',
      enable: true,
      outModes: 'bounce',
      random: false,
      speed: 0.5,
      straight: false
    },
    number: {
      density: {
        enable: true,
      },
      value: 80
    },
    opacity: {
      value: 1
    },
    shape: {
      type: 'circle'
    },
    size: {
      value: { min: 1, max: 6 }
    }
  },
  detectRetina: true
}

const onLoad = (container: Container) => {
  // Do something with the container
  container.pause()
  setTimeout(() => container.play(), 0)
}

const colorMode = useColorMode()

const isDark = computed({
  get() {
    return colorMode.value === 'dark'
  },
  set() {
    colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark'
  }
})

onMounted(() => {
  // play()
})
</script>

<template>
  <div class="relative isolate overflow-hidden bg-white dark:bg-gray-900 min-h-screen transition duration-500">
    <div class="fixed inset-x-0 -top-20 -z-10 transform-gpu overflow-hidden blur-3xl sm:-top-80" aria-hidden="true">
      <div class="relative left-[calc(50%-11rem)] aspect-[1155/678] w-[72.1875rem] -translate-x-1/2 bg-gradient-to-tr from-primary-200 to-primary-400 dark:from-primary-500 dark:to-primary-700 opacity-75 sm:left-[calc(50%-30rem)]" style="clip-path: polygon(74.1% 44.1%, 100% 61.6%, 97.5% 26.9%, 85.5% 0.1%, 80.7% 2%, 72.5% 32.5%, 60.2% 62.4%, 52.4% 68.1%, 47.5% 58.3%, 45.2% 34.5%, 27.5% 76.7%, 0.1% 64.9%, 17.9% 100%, 27.6% 76.8%, 76.1% 97.7%, 74.1% 44.1%)"></div>
    </div>

    <div class="fixed inset-x-0 -bottom-32 -z-10 transform-gpu overflow-hidden blur-3xl " aria-hidden="true">
      <div class="relative left-[calc(50%+3rem)] aspect-[1155/678] w-[72.1875rem] -translate-x-1/2 bg-gradient-to-tr from-primary-200 to-primary-400 dark:from-primary-500 dark:to-primary-700 opacity-75 sm:left-[calc(50%+36rem)]" style="clip-path: polygon(74.1% 44.1%, 100% 61.6%, 97.5% 26.9%, 85.5% 0.1%, 80.7% 2%, 72.5% 32.5%, 60.2% 62.4%, 52.4% 68.1%, 47.5% 58.3%, 45.2% 34.5%, 27.5% 76.7%, 0.1% 64.9%, 17.9% 100%, 27.6% 76.8%, 76.1% 97.7%, 74.1% 44.1%)"></div>
    </div>

    <NuxtParticles
        id="tsparticles"
        :options="options"
        @load="onLoad"
    />


<!--    <div class="fixed inset-x-0">-->
<!--      <slot name="bg" />-->
<!--    </div>-->

<!--    <div class="mx-auto max-w-7xl ">-->
      <div class="mx-auto max-w-7xl lg:grid lg:grid-cols-5 lg:space-x-10 overflow-hidden py-28">
        <div class="lg:col-span-2 px-10 py-5 ">
          <div class="lg:fixed lg:top-0 lg:bottom-0 grid items-center">
            <div class="lg:max-w-lg">
              <ClientOnly>
                <button
                    @click="isDark = !isDark"
                    class="hover:scale-110 rounded-full p-3 transition duration-500"
                >
                  <UIcon
                      :name="isDark ? 'i-fluent-weather-moon-20-regular' : 'i-fluent-weather-sunny-20-regular'"
                      class="text-4xl text-primary "
                  />
                </button>
              </ClientOnly>

              <slot name="left" />
            </div>
          </div>
        </div>

        <div class="lg:col-span-3 px-10 py-7 ">
            <slot name="right" />
        </div>
      </div>

<!--    </div>-->
  </div>
</template>
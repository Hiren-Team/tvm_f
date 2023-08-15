<script setup>
  import { computed, ref } from 'vue'
import { useRouter, useRoute } from 'vue-router';
import Skeleton from '../components/Skeleton.vue';

const router = useRouter()

const aboutData = ref([])
const isLoadingData = ref(true)

const loadAboutData = async () => {
  aboutData.value = (await import('@/data/about.json')).default
  isLoadingData.value = false
}

const formatWord = w => w.replace(w[0], w[0].toUpperCase())

loadAboutData()

const renderAboutData = computed(() => {
  return aboutData.value
})

const months = ['Jan', "Feb", 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
</script>

<template>
    <section class="text-gray-600 body-font">
        <div class="container px-5 pb-24 pt-6 mx-auto">
            <div class="flex flex-col text-left lg:text-center w-full mb-10">
            <h2 class="text-xs text-indigo-500 tracking-widest font-medium title-font mb-1 uppercase">about us</h2>
            <h1 class="sm:text-3xl text-2xl font-medium title-font mb-4 text-gray-900">Discover More about us</h1>
            <p class="lg:w-2/3 lg:mx-auto leading-relaxed text-base">With a heart full of dedication, we assure you that positive change is not just a promise, but our mission.</p>
            </div>

            <div v-if="isLoadingData" class="flex flex-wrap">
              <Skeleton v-for="n in 8" :key="n" class="xl:w-1/4 lg:w-1/2 md:w-full" prefer="card" />
            </div>

            <div v-else class="flex flex-wrap">

                <div v-for="article in renderAboutData" :key="article.id" class="xl:w-1/4 lg:w-1/2 md:w-full px-8 py-6 border-l-2 border-gray-200 border-opacity-60">
                    <article class="flex bg-white transition hover:shadow-xl">
                        <div class="rotate-180 p-2 [writing-mode:_vertical-lr]">
                            <time
                            :datetime="(new Date()).toUTCString()"
                            class="flex items-center justify-between gap-4 text-xs font-bold uppercase text-gray-900"
                            >
                            <span>{{ (new Date()).getFullYear() }}</span>
                            <span class="w-px flex-1 bg-gray-900/10"></span>
                            <span>{{ `${months[(new Date()).getMonth()]} ${(new Date()).getDate()}` }}</span>
                            </time>
                        </div>

                        <div class="hidden sm:block sm:basis-56">
                            <img
                            :alt="article.category"
                            :src="`../src/assets/img/${article.img}`"
                            class="aspect-square h-full w-full object-cover"
                            />
                        </div>

                        <div class="flex flex-1 flex-col justify-between">
                            <div class="border-s border-gray-900/10 p-4 sm:border-l-transparent sm:p-6">
                            <a @click="router.push(`/article/${article.id}`)">
                                <h3 class="font-bold uppercase text-gray-900">
                                {{ article.title }}
                                </h3>
                            </a>

                            <p class="mt-2 line-clamp-3 text-sm/relaxed text-gray-700">
                                {{ article.summary }}
                            </p>
                            </div>

                            <div class="sm:flex sm:items-end sm:justify-end">
                            <a
                                @click="router.push(`/article/${article.id}`)"
                                class="block bg-indigo-400 px-5 py-3 text-center text-xs font-bold uppercase text-gray-900 transition hover:bg-indigo-500"
                            >
                                Read article
                            </a>
                            </div>
                        </div>
                    </article>
                </div>

            </div>
            <button class="flex mx-auto mt-16 text-white bg-indigo-500 border-0 py-2 px-8 focus:outline-none hover:bg-indigo-600 rounded text-lg">More articles</button>
        </div>
    </section>

    <section class="text-gray-700 px-5">
          <div
            class="container max-w-xl p-6 py-12 mx-auto space-y-24 lg:px-8 lg:max-w-7xl"
          >
            <div>
              <h2
                class="text-xl font-bold tracki text-center sm:text-5xl dark:text-gray-50"
              >
                A brief history Of  the Foundation
              </h2>
              <p
                class="max-w-3xl mx-auto mt-4 text-xl text-center dark:text-gray-400"
              >
              Our actions are resolute, and our community's growth is our assurance.
              </p>
            </div>
            <div class="grid lg:gap-8 lg:grid-cols-2 lg:items-center">
              <div>
                <h3 class="text-2xl font-bold tracki sm:text-3xl dark:text-gray-50">
                  Welcome to Tevamuto Foundation
                </h3>
                <p class="mt-3 text-lg dark:text-gray-400">
                  We're on a mission to transform our community into a thriving hub of positivity, progress, and collective growth. With unwavering dedication and a heart for change, we're igniting the spark that lights up lives and paves the way for a brighter tomorrow.
                </p>
                <div class="mt-12 space-y-12">
                  <div class="flex">
                    <div class="flex-shrink-0">
                      <div
                        class="flex items-center justify-center w-12 h-12 rounded-md dark:bg-violet-400 dark:text-gray-900"
                      >
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          fill="none"
                          viewBox="0 0 24 24"
                          stroke="currentColor"
                          class="w-7 h-7"
                        >
                          <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-width="2"
                            d="M5 13l4 4L19 7"
                          ></path>
                        </svg>
                      </div>
                    </div>
                    <div class="ml-4">
                      <h4 class="text-lg font-medium leadi dark:text-gray-50">
                       Our Vision
                      </h4>
                      <p class="mt-2 dark:text-gray-400">
                        To build a community where every member's potential is recognized and nurtured. By fostering an environment of support, inclusivity, and empowerment.
                      </p>
                    </div>
                  </div>
                  <div class="flex">
                    <div class="flex-shrink-0">
                      <div
                        class="flex items-center justify-center w-12 h-12 rounded-md dark:bg-violet-400 dark:text-gray-900"
                      >
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          fill="none"
                          viewBox="0 0 24 24"
                          stroke="currentColor"
                          class="w-7 h-7"
                        >
                          <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-width="2"
                            d="M5 13l4 4L19 7"
                          ></path>
                        </svg>
                      </div>
                    </div>
                    <div class="ml-4">
                      <h4 class="text-lg font-medium leadi dark:text-gray-50">
                        Our Mission
                      </h4>
                      <p class="mt-2 dark:text-gray-400">
                        Collectively, we envision a community where education,women empowerment, sports, and agriculture come together to create a tapestry of growth and progres through collaboration, compassion, and action.</p>
                    </div>
                  </div>
                  <div class="flex">
                    <div class="flex-shrink-0">
                      <div
                        class="flex items-center justify-center w-12 h-12 rounded-md dark:bg-violet-400 dark:text-gray-900"
                      >
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          fill="none"
                          viewBox="0 0 24 24"
                          stroke="currentColor"
                          class="w-7 h-7"
                        >
                          <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-width="2"
                            d="M5 13l4 4L19 7"
                          ></path>
                        </svg>
                      </div>
                    </div>
                    <div class="ml-4">
                      <h4 class="text-lg font-medium leadi dark:text-gray-50">
                        What we Do
                      </h4>
                      <p class="mt-2 dark:text-gray-400">
                        Our hands-on approach ensures that our impact is felt on the ground, enriching lives in ways that resonate far beyond our immediate reach.
                      </p>
                    </div>
                  </div>
                </div>
              </div>
              <div aria-hidden="true" class="mt-10 lg:mt-0">
                <img
                  src="https://source.unsplash.com/random/360x480"
                  alt=""
                  class="mx-auto rounded-lg shadow-lg dark:bg-gray-500"
                />
              </div>
            </div>
            <div>
              <div class="grid lg:gap-8 lg:grid-cols-2 lg:items-center">
                <div class="lg:col-start-2">
                  <h3 class="text-2xl font-bold tracki sm:text-3xl dark:text-gray-50">
                    Brief Background of the Foundation
                  </h3>
                  <p class="mt-3 text-lg dark:text-gray-400">
                    (................................................................)
                  </p>
                  <div class="mt-12 space-y-12">
                    <div class="flex">
                      <div class="flex-shrink-0">
                        <div
                          class="flex items-center justify-center w-12 h-12 rounded-md dark:bg-violet-400 dark:text-gray-900"
                        >
                          <svg
                            xmlns="http://www.w3.org/2000/svg"
                            fill="none"
                            viewBox="0 0 24 24"
                            stroke="currentColor"
                            class="w-7 h-7"
                          >
                            <path
                              stroke-linecap="round"
                              stroke-linejoin="round"
                              stroke-width="2"
                              d="M5 13l4 4L19 7"
                            ></path>
                          </svg>
                        </div>
                      </div>
                      <div class="ml-4">
                        <h4 class="text-lg font-medium leadi dark:text-gray-50">
                          Community Building
                        </h4>
                        <p class="mt-2 dark:text-gray-400">
                          Together, we're more than just a sum of our parts. Our sense of community strengthens bonds and creates lasting connections.
                        </p>
                      </div>
                    </div>
                    <div class="flex">
                      <div class="flex-shrink-0">
                        <div
                          class="flex items-center justify-center w-12 h-12 rounded-md dark:bg-violet-400 dark:text-gray-900"
                        >
                          <svg
                            xmlns="http://www.w3.org/2000/svg"
                            fill="none"
                            viewBox="0 0 24 24"
                            stroke="currentColor"
                            class="w-7 h-7"
                          >
                            <path
                              stroke-linecap="round"
                              stroke-linejoin="round"
                              stroke-width="2"
                              d="M5 13l4 4L19 7"
                            ></path>
                          </svg>
                        </div>
                      </div>
                      <div class="ml-4">
                        <h4 class="text-lg font-medium leadi dark:text-gray-50">
                          Collaboration:
                        </h4>
                        <p class="mt-2 dark:text-gray-400">
                          We work hand in hand with local partners, businesses, and volunteers, creating a network of support that propels our community forward.
                        </p>
                      </div>
                    </div>
                    <div class="flex">
                      <div class="flex-shrink-0">
                        <div
                          class="flex items-center justify-center w-12 h-12 rounded-md dark:bg-violet-400 dark:text-gray-900"
                        >
                          <svg
                            xmlns="http://www.w3.org/2000/svg"
                            fill="none"
                            viewBox="0 0 24 24"
                            stroke="currentColor"
                            class="w-7 h-7"
                          >
                            <path
                              stroke-linecap="round"
                              stroke-linejoin="round"
                              stroke-width="2"
                              d="M5 13l4 4L19 7"
                            ></path>
                          </svg>
                        </div>
                      </div>
                      <div class="ml-4">
                        <h4 class="text-lg font-medium leadi dark:text-gray-50">
                          Sustainability
                        </h4>
                        <p class="mt-2 dark:text-gray-400">
                          Whether it's through green initiatives or educational programs, we're committed to sustainable practices that pave the way for a better future.
                        </p>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="mt-10 lg:mt-0 lg:col-start-1 lg:row-start-1">
                  <img
                    src="https://source.unsplash.com/random/361x481"
                    alt=""
                    class="mx-auto rounded-lg shadow-lg dark:bg-gray-500"
                  />
                </div>
              </div>
            </div>
          </div>
      </section>


</template>
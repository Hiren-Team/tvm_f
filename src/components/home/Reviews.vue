<script setup>
import { defineAsyncComponent, ref } from 'vue';
import Skeleton from '../Skeleton.vue';

const openReviewsModal = ref(false)
// const newReviewForm = defineAsyncComponent(() => import(''))
const loadData = async () => {
  return new Promise(res => setTimeout(res({title: 'hello MthF'}), 8000))
}

</script>

<template>
    <section class="px-10 py-4">
      <div class="flex flex-col text-left lg:text-center w-full mb-10">
              <h2 class="text-xs text-indigo-500 tracking-widest font-medium title-font mb-1 uppercase">What People Say</h2>
              <h1 class="sm:text-3xl text-2xl font-medium title-font mb-4 text-gray-900">Here is what people say about the Organisation</h1>
              </div>
        <div class="mx-auto max-w-screen-xl">

          <Suspense>
            <template #fallback>
              <div class="max-h-96 gap-2 overflow-auto lg:overflow-y-hidden [column-fill:_balance] lg:columns-3 lg:gap-8">
                <div v-for="n in 10" class="mb-8 break-inside-avoid lg">
                    <Skeleton prefer="card" />
                  </div>
              </div>
            </template>

            <template #default>        
              <div class="max-h-96 gap-2 overflow-auto lg:overflow-y-hidden [column-fill:_balance] lg:columns-3 lg:gap-8">
                
                <div class="mb-8 break-inside-avoid lg">
                  <blockquote class="rounded-xl lg:mx-auto bg-gray-50 p-6 shadow">
                    <p class="leading-relaxed text-gray-700">
                      "I've volunteered with Tevamuto Foundation for some time, and it has changed my perspective on community service. Seeing the impact of our collective efforts, from educational workshops to local clean-up drives, makes me proud to be part of such a purpose-driven family." </p>
                  </blockquote>

                  <div class="mt-4 flex items-center text-gray-600 gap-4">
                    <img
                      alt="Woman"
                      src="@/assets/img/user.jpg"
                      class="h-12 w-12 rounded-full object-cover"
                    />

                    <div class="text-sm">
                      <p class="font-medium">Kiryowa Duncan </p>
                      <p class="mt-1">Youth Chairman</p>
                    </div>
                  </div>
                </div>

                <div class="mb-8 sm:break-inside-avoid">
                  <blockquote class="rounded-xl bg-gray-50 p-6 shadow">
                    <p class="leading-relaxed text-gray-700">
                      "Before Tevamuto Foundation's Agricultural projects, I had no idea about sustainable farming. Now, I grow my own vegetables, reduce my carbon footprint, and even educate my family. It's a small step for me, but a huge leap for our environment."
                    </p>
                  </blockquote>

                  <div class="mt-4 flex items-center text-gray-600 gap-4">
                    <img
                      alt="Woman"
                      src="@/assets/img/user.jpg"
                      class="h-12 w-12 rounded-full object-cover"
                    />

                    <div class="text-sm">
                      <p class="font-medium">Onen Gideon</p>
                      <p class="mt-1">Farmer</p>
                    </div>
                  </div>
                </div>

                <div class="mb-8 sm:break-inside-avoid">
                  <blockquote class="rounded-xl bg-gray-50 p-6 shadow">
                    <p class="leading-relaxed text-gray-700">
                      Their programs, especially the sports clinics and mentorship initiatives, have sparked dreams in young hearts and taught them values that extend well beyond the court. I've had the privilege of witnessing firsthand the transformation that takes place when a child realizes their potential.</p>
                  </blockquote>

                  <div class="mt-4 flex items-center text-gray-600 gap-4">
                    <img
                      alt="Woman"
                      src="@/assets/img/user.jpg"
                      class="h-12 w-12 rounded-full object-cover"
                    />

                    <div class="text-sm">
                      <p class="font-medium">Alani Moses</p>
                      <p class="mt-1">Football Coach</p>
                    </div>
                  </div>
                </div>

                <div class="mb-8 sm:break-inside-avoid">
                  <blockquote class="rounded-xl bg-gray-50 p-6 shadow">
                    <p class="leading-relaxed text-gray-700">
                      Through their initiatives, I've been able to not only share my art but also connect with fellow creators who understand the significance of our heritage.Tevamuto Foundation's  support has given me a platform to bridge the gap between generations, ensuring that our traditions continue to thrive.</p>
                  </blockquote>

                  <div class="mt-4 flex items-center text-gray-600 gap-4">
                    <img
                      alt="Woman"
                      src="@/assets/img/user.jpg"
                      class="h-12 w-12 rounded-full object-cover"
                    />

                    <div class="text-sm">
                      <p class="font-medium">Nambi Evelyn</p>
                      <p class="mt-1">Culturalist</p>
                    </div>
                  </div>
                </div>

                <div class="mb-8 sm:break-inside-avoid">
                  <blockquote class="rounded-xl bg-gray-50 p-6 shadow">
                    <p class="leading-relaxed text-gray-700">
                    Tevamuto Foundation has nurtured character, values, and a sense of literacy in all of us. Through various extracurricular activities and community service projects, they've instilled in us the importance of giving back,being responsible and educated global citizens.
                    </p>
                  </blockquote>

                  <div class="mt-4 flex items-center text-gray-600 gap-4">
                    <img
                      alt="Woman"
                      src="@/assets/img/user.jpg"
                      class="h-12 w-12 rounded-full object-cover"
                    />

                    <div class="text-sm">
                      <p class="font-medium">Kimbowa Fred</p>
                      <p class="mt-1">Teacher</p>
                    </div>
                  </div>
                </div>

                <div class="mb-8 sm:break-inside-avoid">
                  <blockquote class="rounded-xl bg-gray-50 p-6 shadow">
                    <p class="leading-relaxed text-gray-700">
                      I stand today as a testament to their efforts – a woman who is not just empowered, but also inspired to uplift others. Thank you, Tevamuto Foundation, for believing in us and giving us the tools to shape our own destinies."
                    </p>
                  </blockquote>

                  <div class="mt-4 flex items-center text-gray-600 gap-4">
                    <img
                      alt="Woman"
                      src="@/assets/img/user.jpg"
                      class="h-12 w-12 rounded-full object-cover"
                    />

                    <div class="text-sm">
                      <p class="font-medium">Nantume Priscilla</p>
                      <p class="mt-1">Trailblazing Champion of Women Empowermment</p>
                    </div>
                  </div>
                </div>
              </div>
            </template>
          

          </Suspense>
        </div>
        <button class="flex mx-auto mt-16 text-white bg-indigo-500 border-0 py-2 px-8 focus:outline-none hover:bg-indigo-600 rounded text-lg">Add your review</button>
      </section>
</template>
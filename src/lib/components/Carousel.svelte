<script>
  const IMAGE_BASE_URL = 'https://image.tmdb.org/t/p/original'

  import { onMount } from "svelte";
  const endpoint = 'https://api.themoviedb.org/3/trending/all/day?api_key=1b7867a22a2071d3058b7ac05a739997';
  let data
  onMount(async function () {
    const response = await fetch(endpoint);
    const data = await response.json();
    // console.log("series",data);

  });
</script>

<div
  class="mb-6 flex flex-col justify-between mt-4 bg-black/10 bg-blend-multiply rounded-lg overflow-hidden bg-cover bg-center text-white"
  style="background-image: url('/inception.jpg'); height: 360px;">
  <!-- <img class="object-cover rounded-lg h-full w-full" src="/inception.jpg" alt=""> -->
  <div class="hidden flex -space-x-1 items-center ">
    <img class="rounded-full w-7 h-7 shadow-lg border border-white"
      src="https://api.lorem.space/image/face?w=32&amp;h=32&amp;hash=zsrj8csk" alt="" srcset="">
    <img class="rounded-full w-7 h-7 shadow-lg border border-white"
      src="https://api.lorem.space/image/face?w=32&amp;h=32&amp;hash=zsrj8cck" alt="" srcset="">
    <img class="rounded-full w-7 h-7 shadow-lg border border-white"
      src="https://api.lorem.space/image/face?w=32&amp;h=32&amp;hash=zsfj8cck" alt="" srcset="">
    <span class="pl-4 text-xs drop-shadow-lg">+8 friends are watching</span>
  </div>

  <div class="flex float-right p-6">
    <svg
      class="m-1 h-7 w-7 rounded-full border p-1 hover:border-red-600 hover:fill-red-600 dark:fill-white dark:hover:fill-red-600"
      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
      <path d="M13.293 6.293L7.58 12l5.7 5.7 1.41-1.42 -4.3-4.3 4.29-4.293Z"></path>
    </svg>
    <svg
      class="m-1 h-7 w-7 rounded-full border p-1 hover:border-red-600 hover:fill-red-600 dark:fill-white dark:hover:fill-red-600"
      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
      <path d="M10.7 17.707l5.7-5.71 -5.71-5.707L9.27 7.7l4.29 4.293 -4.3 4.29Z"></path>
    </svg>
  </div>

  <div class="bg-gradient-to-r from-black/30 to-transparent p-6">
    <span class="uppercase text-3xl font-semibold drop-shadow-lg ">Inception</span>
    <div class="text-xs text-gray-200 mt-2">
      <a href="#" class="">Action</a>,
      <a href="#" class="">Adventure</a>,
      <a href="#" class="">Sci-Fi</a>
    </div>
  </div>
</div>
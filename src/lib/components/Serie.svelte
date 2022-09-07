<script>
  export let serie
  import Comments from "./Comment.svelte";
  
  const IMAGE_BASE_URL = 'https://image.tmdb.org/t/p/original'

</script>
<div
  class="flex flex-col justify-between mt-4 bg-black/10 bg-blend-multiply rounded-lg overflow-hidden bg-cover bg-center text-white h-auto"
  style="">
  <img class="object-cover rounded-lg w-full" style="height:360px" src={`${IMAGE_BASE_URL}${serie.backdrop_path}`} alt="">
  <div class="hidden flex -space-x-1 items-center ">
    <img class="rounded-full w-7 h-7 shadow-lg border border-white"
      src="https://api.lorem.space/image/face?w=32&amp;h=32&amp;hash=zsrj8csk" alt="" srcset="">
    <img class="rounded-full w-7 h-7 shadow-lg border border-white"
      src="https://api.lorem.space/image/face?w=32&amp;h=32&amp;hash=zsrj8cck" alt="" srcset="">
    <img class="rounded-full w-7 h-7 shadow-lg border border-white"
      src="https://api.lorem.space/image/face?w=32&amp;h=32&amp;hash=zsfj8cck" alt="" srcset="">
    <span class="pl-4 text-xs drop-shadow-lg">+8 friends are watching</span>
  </div>
  <div class="bg-gradient-to-r from-black/30 to-transparent p-6">
    <a href={`#/serie/${serie.id}`}>
      <span class="uppercase text-3xl font-semibold drop-shadow-lg ">{serie.name}</span>
    </a>
    <div class="text-xs text-gray-200 mt-2">
      <a href="#" class="">Action</a>,
      <a href="#" class="">Adventure</a>,
      <a href="#" class="">Sci-Fi</a>
    </div>

    <!-- <Comments /> -->

    <div class="flex float-right">
      <a href={`#/serie/${serie.id}`}>View Details</a>
    </div>
  </div>
</div>
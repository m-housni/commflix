<script>
  export let serie

  import Comment from "./Comment.svelte";
  
  const url = `https://api.themoviedb.org/3/tv/${serie.id}/reviews?api_key=1b7867a22a2071d3058b7ac05a739997`
  let serieReviews = fetch(url).then((x) => x.json())
  
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

    <!-- <Comments /> -->
    {#await serieReviews}
          ...
    {:then reviews}
      {#if reviews.results.length === 0}
        <div class="mt-6">
          Pas de commentaire, soyez le premier à en laisser un !
        </div>
      {:else}
      {#each reviews.results.splice(0,10) as review, i}
      <span class="block text-3xl font-semibold drop-shadow-lg mt-6">Reviews</span>
        <Comment {review} />
      {/each}
      {/if}
    {/await}
  </div>
</div>
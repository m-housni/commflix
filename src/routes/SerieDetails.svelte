<script>

import Main from "../lib/Main.svelte"
import CommentForm from "../lib/components/CommentForm.svelte"
import AsideLeft from "../lib/AsideLeft.svelte"
import AsideRight from "../lib/AsideRight.svelte"
import Comment from "../lib/components/Comment.svelte";

  export let params = {}

  const serieId = params.id

  const IMAGE_BASE_URL = 'https://image.tmdb.org/t/p/original'
  const url1 = `https://api.themoviedb.org/3/tv/${serieId}?api_key=1b7867a22a2071d3058b7ac05a739997`
  let serieDetails = fetch(url1).then((x) => x.json())
  const url2 = `https://api.themoviedb.org/3/tv/${serieId}/reviews?api_key=1b7867a22a2071d3058b7ac05a739997`
  let serieReviews = fetch(url2).then((x) => x.json())
  const url3 = `https://api.themoviedb.org/3/tv/${serieId}/images?api_key=1b7867a22a2071d3058b7ac05a739997`
  const posters = fetch(url3).then((x) => x.json())

  // fetch serie details

</script>

<div class="flex min-h-screen  2xl:max-w-screen-2xl 2xl:mx-auto 2xl:border-x-2 2xl:border-gray-200 dark:2xl:border-zinc-700 ">
 
  <!-- <AsideLeft /> -->

  <Main>
    {#await serieDetails}
      Fetching Data
    {:then serie}
      <div
      class="flex flex-col justify-between mt-4 bg-black/10 bg-blend-multiply rounded-lg overflow-hidden bg-cover bg-center text-white h-auto"
      style="">
      <img class="object-cover rounded-lg w-full" style="height:360px" src={`${IMAGE_BASE_URL}${serie?.backdrop_path ?? serie?.poster_path}`} alt="">

      {#await posters}
        ...
      {:then data}
        <div class="flex">
        {#each data.posters as poster}
          <img class="object-cover rounded-lg w-1/6"src={`${IMAGE_BASE_URL}${poster.file_path}`} alt="">
        {/each}
        </div>
      {/await}

      <div class="bg-gradient-to-r from-black/30 to-transparent p-6">
        
        <span class="uppercase text-3xl font-semibold drop-shadow-lg ">{serie.tagline}</span>
        <span class="block text-md font-semibold drop-shadow-lg text-gray-400">{serie.overview}</span>

        <div class="flex items-center mt-2">
          <span class="text-sm text-gray-400 drop-shadow-lg">{serie.release_date}</span>
          <span class="text-sm text-gray-400 drop-shadow-lg mx-2">•</span>
          <span class="text-sm text-gray-400 drop-shadow-lg">{serie.vote_average}</span>
          <span class="text-sm text-gray-400 drop-shadow-lg mx-2">•</span>
          <span class="text-sm text-gray-400 drop-shadow-lg">{serie.vote_count}</span>
        </div>

        <div class="text-xs text-gray-200 mt-2">
          {#each serie.genres as genre, i}
            {#if i < serie.genres.length - 1 }
              {genre.name},&nbsp; 
            {:else}
              {genre.name}
            {/if}
          {/each}
        </div>

        <div class="text-xs text-gray-200 mt-2">
          {#each serie.production_companies as company, i}
            {#if i < serie.production_companies.length - 1 }
              {company.name},&nbsp; 
            {:else}
              {company.name}
            {/if}
          {/each}
        </div>

        {#await serieReviews}
          ...
        {:then reviews}
          {#if reviews.results.length === 0}
            <div class="mt-6">
              Pas de commentaire, soyez le premier à en laisser un !
            </div>
          {:else}
          {#each reviews.results as review, i}
          <span class="block text-3xl font-semibold drop-shadow-lg mt-6">Reviews</span>
            <Comment {review} />
          {/each}
          {/if}
        {/await}
        <CommentForm />
      </div>
    </div>
    {/await}
  </Main>

  <!-- <AsideRight /> -->
</div>

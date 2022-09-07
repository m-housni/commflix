<script>

import AsideLeft from "../lib/AsideLeft.svelte"
import Main from "../lib/Main.svelte"
import AsideRight from "../lib/AsideRight.svelte"
import Carousel from "../lib/components/Carousel.svelte"
import Serie from "../lib/components/Serie.svelte"

  const endpoint = 'https://api.themoviedb.org/3/trending/tv/day?api_key=1b7867a22a2071d3058b7ac05a739997';
  let promise = fetch(endpoint).then((x) => x.json());

</script>


<div class="flex min-h-screen  2xl:max-w-screen-2xl 2xl:mx-auto 2xl:border-x-2 2xl:border-gray-200 dark:2xl:border-zinc-700 ">
 
  <!-- <AsideLeft /> -->

  <Main>
    <Carousel />
    {#await promise}
      Fetching Data
    {:then data}
      {#each data.results as serie}
      <Serie {serie} />
      {/each}
    {/await}
  </Main>

  <AsideRight />
</div>


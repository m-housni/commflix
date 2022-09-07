<script>
  const IMAGE_BASE_URL = 'https://image.tmdb.org/t/p/original'
  const url = `https://api.themoviedb.org/3/trending/tv/day?api_key=1b7867a22a2071d3058b7ac05a739997`
  $: trending = fetch(url).then((x) => x.json())

  $: i = 1

  const next = () => {
    if(i>=5) i = 0
    i++ 
  }
  const prev = () => {
    if(i==0) i = 5
    i--
  }

</script>

{#await trending}
...
{:then data}
<div
  class="mb-6 flex flex-col justify-between mt-4 bg-black/10 bg-blend-multiply rounded-lg overflow-hidden bg-cover bg-center text-white"
  style={`background-image: url(${IMAGE_BASE_URL}${data.results[i].backdrop_path}); height: 560px;`}>
  <!-- <img class="object-cover rounded-lg h-full w-full" src="/inception.jpg" alt=""> -->
  <div class="flex float-right p-6">
    <svg on:click={prev}
      class="m-1 h-7 w-7 rounded-full border p-1 hover:border-red-600 hover:fill-red-600 dark:fill-white dark:hover:fill-red-600"
      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
      <path d="M13.293 6.293L7.58 12l5.7 5.7 1.41-1.42 -4.3-4.3 4.29-4.293Z"></path>
    </svg>
    <svg on:click={next}
      class="m-1 h-7 w-7 rounded-full border p-1 hover:border-red-600 hover:fill-red-600 dark:fill-white dark:hover:fill-red-600"
      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
      <path d="M10.7 17.707l5.7-5.71 -5.71-5.707L9.27 7.7l4.29 4.293 -4.3 4.29Z"></path>
    </svg>
  </div>

  <div class="bg-gradient-to-r from-black/30 to-transparent p-6">
    <a href={`/#/serie/${data.results[i].id}`}>
      <span class="uppercase text-3xl font-semibold drop-shadow-lg ">{data.results[i].name}</span>
    </a>
    <div class="text-sm text-gray-300">
      {data.results[i].overview}
    </div>
    <div class="text-xs text-gray-200 mt-2">
      {data.results[i].original_language} | <span>{data.results[i].origin_country}</span>
    </div>
  </div>
</div>
{/await}
<script>
  export let review = {}
    const IMAGE_BASE_URL = 'https://image.tmdb.org/t/p/original'
</script>


<div class="mt-4 bg-gray-900 rounded-lg px-2">
  <p class="mt-4 p-6 text-md text-white">{review.content}</p>
  <div class="flex justify-between items-center p-6">
    <div class="flex items-center space-x-4 pt-6">
      <div class="">
        <img class="w-12 h-12 rounded-full" src={review?.author_details?.avatar_path ? `${IMAGE_BASE_URL}/${review.author_details.avatar_path}` : 'https://cdn.cloudflare.steamstatic.com/steamcommunity/public/images/avatars/54/54cdbf27ef827822eb34715fde4457ebd772311d.jpg'} alt="" />
      </div>
      <div class="text-sm font-semibold">{review.author} • <span class="font-normal"> {review.created_at}</span></div>
    </div>
    <div class="flex items-center justify-center text-2xl text-white mt-4 shadow-lg cursor-pointer">
      <div class="flex mt-2">
        <div class="flex w-12 h-12 rounded-full bg-yellow-700 text-white center text-sm">
          <div class="m-auto font-bold">{review.author_details.rating}/10</div>
        </div>
      </div>
    </div>
  </div>
</div>
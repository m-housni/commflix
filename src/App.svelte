<script>
  import Router from 'svelte-spa-router'

  import SerieDetails from './routes/SerieDetails.svelte'
  import HomePage from './routes/HomePage.svelte'
  import NotFound from './routes/NotFound.svelte'


  const routes = {

    '/': HomePage,
    '/serie/:id': SerieDetails,

    //...

    '*': NotFound,

  }
</script>

<Router {routes} />
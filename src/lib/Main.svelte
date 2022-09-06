<script>
  import Header from "./components/Header.svelte";
</script>

<main class=" flex-1 py-10  px-5 sm:px-10 ">

    
    <Header />

    <section>
      <nav class="flex space-x-6 text-gray-400 font-medium">
        <a href="#/serie" class="hover:text-gray-700 dark:hover:text-white">TANDANCES (A LA UNE)</a>
      </nav>
      <slot/>
    </section>
  </main>


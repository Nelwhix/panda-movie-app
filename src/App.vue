<script>
import Navigation from "./components/Navigation.vue"
import SearchBar from "./components/SearchBar.vue"
import MovieListVue from "./components/MovieList.vue"

export default {
  components: {
    Navigation,
    SearchBar,
    MovieListVue
  }
}
</script>

<template>
  <Navigation />
  <main class="">
    <div class="m-3">
      <h2 class="text-center font-body font-semibold text-xl m-5 text-gray-600">All the movies you can want, on one site!</h2>
    </div>
		<SearchBar />
    <MovieListVue />
  </main>
</template>
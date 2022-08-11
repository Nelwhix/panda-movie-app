<script>
export default {
    name: 'SearchBar',
    data() {
        return {
            error: null,
            errorMessage: 'Type a movie name to search',
            searchInput: null,
            isClicked: false,
            movies: []
        }
    },
    methods: {
        checkForm() {
            if (!this.searchInput) {
                this.error = true;
            } else {
                this.searchMovie(this.searchInput);
            }
        },
      async searchMovie(input) {
          let res = await fetch('https://pan-da.herokuapp.com/api/search/' + input)
		  if (res) {
			this.isClicked = !this.isClicked
		  }
          let data = await res.json()
          this.movies = data;
          this.searchInput=""
      },
      spin() {
        this.isClicked = !this.isClicked
      }
    }
}
</script>

<template>
    <section class="mt-3">
        <form id="search" class="flex justify-center" @submit.prevent="checkForm">
            <div class="relative w-80 md:w-96">
                <input id="searchInput" v-model="searchInput" type="text" class="p-3 pl-3 border-2 border-gray-300 rounded-full w-80 md:w-96 text-sm focus:outline-blue-300" placeholder="Search Movie/TV Show name">
                <button type="submit" class="absolute top-0 right-2 md:right-2">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 ml-1 mt-3 text-gray-500" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
                    </svg>
                </button>
                <p class="text-red-500 font-body text-sm" v-if="this.error">{{this.errorMessage}}</p>
            </div>
			</form>
    </section>
</template>

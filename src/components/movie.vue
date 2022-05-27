<template>
  <div class="bg-black text-white p-20">
    <div class="container mx-auto">
      <div class="flex justify-evenly items-center">
        <div class="block">
          <h1 class="text-3xl font-bold mb-4">{{ movies[curID].title }}</h1>
          <div class="flex items-center justify-between py-3 border-t border-b border-gray-300">
            <div>
              <h2 class="text-xl uppercase mb-3">Metascore</h2>
              <p class="w-2/3">Universal acclaim based on 18 Critic Reviews</p>
            </div>
            <div class="flex items-center">
              <img
                class="w-16"
                v-if="movies[curID].mustsee === true"
                src="https://www.metacritic.com/images/icons/mc-mustsee-sm.svg"
                alt=""
              />
              <p class="bg-green-400 text-white text-xl font-semibold p-3 rounded-md ml-4">
                {{ movies[curID].rate }}
              </p>
            </div>
          </div>
          <div class="flex items-center justify-between py-3 border-b border-gray-300">
            <div>
              <h2 class="text-xl uppercase mb-3">User Score</h2>
              <p class="w-2/3">Universal acclaim based on 18 Critic Reviews</p>
            </div>
            <div class="flex items-center">
              <p class="bg-green-400 text-white text-xl font-semibold p-3 rounded-md">
                {{ movies[curID].user }}
              </p>
            </div>
          </div>
        </div>
        <video class="w-1/2" muted autoplay controls :src="movies[curID].video"></video>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      movies: [],
      baseURL: "http://localhost:3001/movies",
      curID: this.$route.params.id - 1,
    };
  },
  async mounted() {
    try {
      const res = await axios.get(this.baseURL);
      this.movies = res.data;
    } catch (e) {
      console.error(e);
    }
    console.log(this.movies);
  },
};
</script>
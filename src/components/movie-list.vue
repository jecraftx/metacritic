<template>
  <div class="container mx-auto">
    <div
      class="border-b py-8 border-gray-300"
      v-for="movie of movies"
      :key="movie.id"
    >
      <div
        @click="$router.push({ name: 'Movie', params: { id: movie.id } })"
        class="flex items-start"
      >
        <div class="mr-4 relative">
          <img :src="movie.img" alt="" />
          <img
            class="mustsee_movie"
            v-if="movie.mustsee === true"
            src="https://www.metacritic.com/images/icons/mc-mustsee-sm.svg"
            alt=""
          />
        </div>
        <div class="block w-full">
          <h2 class="text-xl font-semibold">
            {{ movie.id }}. {{ movie.title }}
          </h2>
          <p class="my-2 text-gray-400">{{ movie.date }}</p>
          <p>{{ movie.desc }}</p>
        </div>
        <p class="bg-green-400 text-white text-xl font-semibold p-3 rounded-md">
          {{ movie.rate }}
        </p>
      </div>
    </div>
    <form class="my-20" action="">
      <h1 class="text-3xl font-bold my-4">Enter new data</h1>
      <p class="font-bold my-2">Enter title...</p>
      <input
        class="border border-gray-300 text-lg w-full p-3 rounded-lg"
        type="text"
        v-model="form.title"
      />
      <p class="font-bold my-2">Enter date...</p>
      <input
        class="border border-gray-300 text-lg w-full p-3 rounded-lg"
        type="text"
        v-model="form.date"
      />
      <p class="font-bold my-2">Enter description...</p>
      <input
        class="border border-gray-300 text-lg w-full p-3 rounded-lg"
        type="text"
        v-model="form.desc"
      />
      <p class="font-bold my-2">Enter metascore...</p>
      <input
        class="border border-gray-300 text-lg w-full p-3 rounded-lg"
        type="text"
        v-model="form.rate"
      />
      <p class="font-bold my-2">Enter userscore...</p>
      <input
        class="border border-gray-300 text-lg w-full p-3 rounded-lg"
        type="text"
        v-model="form.user"
      />
      <p class="font-bold my-2">Enter img url...</p>
      <input
        class="border border-gray-300 text-lg w-full p-3 rounded-lg"
        type="text"
        v-model="form.img"
      />
      <p class="font-bold my-2">Enter video url...</p>
      <input
        class="border border-gray-300 text-lg w-full p-3 rounded-lg"
        type="text"
        v-model="form.video"
      />
      <p class="font-bold my-2">Enter mustsee...</p>
      <!-- <select v-model="form.mustsee" name="" id="">
          <option value=true>True</option>
          <option value=false>False</option>
      </select> -->
      <input type="checkbox" value=true v-model="form.mustsee">
      <button
        class="
          bg-green-400
          text-white
          px-20
          py-3
          text-2xl
          flex
          mx-auto
          rounded-lg
          mt-4
        "
        @click="addMovie()"
      >
        Commit movie
      </button>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      movies: [],
      baseURL: "http://localhost:3001/movies",
      form: {
        title: "",
        date: "",
        desc: "",
        rate: 0,
        user: 0,
        img: "",
        mustsee: false,
        video: "",
      },
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
  methods: {
    async addMovie() {
      try {
        const res = await axios.post(this.baseURL, {
          title: this.form.title,
          date: this.form.date,
          desc: this.form.desc,
          rate: this.form.rate,
          user: this.form.user,
          img: this.form.img,
          mustsee: this.form.mustsee,
          video: this.form.video,
        });
        this.movies = [...this.movies, res.data];
      } catch (e) {
        console.error(e);
      }
    },
  },
};
</script>